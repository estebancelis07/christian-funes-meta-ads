Sales Velocity Report — Weekly unified report correlating Meta Ads campaigns with GoHighLevel pipeline data. Extracts campaign/ad-level performance, GHL lead stages, and generates a premium branded HTML report with week-over-week comparisons and detailed action items with responsibles.

\# /sales-velocity-report — Weekly Ads-to-Pipeline Performance Report

\#\# Overview  
This workflow generates a \*\*weekly Sales Velocity Report\*\* for a client. It unifies Meta Ads campaign data with GHL pipeline stages to provide a complete view of the acquisition funnel.

\*\*Replaces:\*\* \`/meta-ads-review\` (which still works as alias)

\*\*Key features:\*\*  
\- Always includes \*\*GHL pipeline correlation\*\* (mandatory, not optional)  
\- \*\*Week-over-week comparisons\*\* with deltas, trend arrows, and narrative  
\- \*\*Campaign \+ Ad-level breakdown\*\* with active/paused ads and reasons for pausing  
\- \*\*Lead-by-lead detail\*\* linking each Meta lead to their GHL pipeline stage  
\- \*\*Lead quality scoring\*\* (qualified, pending, disqualified, lost)  
\- \*\*Detailed action items\*\* with responsible person, steps, expected impact, effort, and deadline  
\- \*\*Previous report JSON\*\* is parsed automatically for comparison

\*\*Principles:\*\*  
\- Each report is \*\*immutable\*\* — once created, never modified  
\- Each new report \*\*compares against the previous\*\* (week-over-week deltas)  
\- Reports are \*\*branded\*\* per client (colors, fonts, logo from Brand Manual)  
\- Self-contained HTML deployed to GitHub Pages  
\- Naming: \`sv\_report\_\[YYYY-MM-DD\].html\`

\*\*NotebookLM Notebook ID:\*\* \`6aab2459-81ea-406f-b46d-59ac8ecc4fc0\`

\---

\#\# Prerequisites  
\- \[ \] Client in \`clients\_config.json\` with valid GHL \+ Meta credentials  
\- \[ \] Client has Brand Manual in \`01\_marca/\`  
\- \[ \] Client has Base de Conocimiento in \`06\_docs/\`  
\- \[ \] Meta Ads token is VALID (not expired)  
\- \[ \] GHL API Key is VALID

\---

\#\# Steps

\#\#\# STEP 0: Load Client Context & Previous Report  
// turbo

1\. \*\*Read Base de Conocimiento\*\* from \`06\_docs/base\_de\_conocimiento\_\[client\].md\`  
2\. \*\*Read Brand Manual\*\* from \`01\_marca/\`  
3\. \*\*Check for previous reports\*\* in \`07\_meta\_reviews/\`:  
   \`\`\`bash  
   ls \-t \~/Desktop/Clientes/\[CLIENT\]/07\_meta\_reviews/sv\_report\_\*.html 2\>/dev/null | head \-1  
   ls \-t \~/Desktop/Clientes/\[CLIENT\]/07\_meta\_reviews/meta\_review\_\*.html 2\>/dev/null | head \-1  
   \`\`\`  
   \- If previous exists: parse \`\<script id="review-data"\>\` JSON for delta calculations  
   \- If none: this is BASELINE (no deltas, show "BASELINE" badges)  
4\. Create \`07\_meta\_reviews/\` if needed

\---

\#\#\# 🚨 STEP 0.5: META ADS ACCESS GATE (MANDATORY — NEVER SKIP)

\> \[\!CAUTION\]  
\> \*\*HARD GATE — DO NOT PROCEED PAST THIS STEP\*\* unless BOTH validations pass OR the user explicitly says \`--force\` or "avanza sin Meta Ads".  
\> Running this workflow without Meta Ads data produces an incomplete report. It's a waste of time.

\*\*Validation 1 — Token validity:\*\*  
\`\`\`bash  
TOKEN=$(python3 \-c "import json; print(json.load(open('$HOME/Desktop/Clientes/LuchoBranding/config/clients\_config.json'))\['meta\_app\_token'\])")  
curl \-s "https://graph.facebook.com/v22.0/debug\_token?input\_token=${TOKEN}\&access\_token=${TOKEN}" | python3 \-m json.tool  
\`\`\`  
\- ✅ \`is\_valid: true\` → pass  
\- ❌ \`is\_valid: false\` or error → \*\*HARD STOP\*\* → tell user token expired, follow renewal procedure

\*\*Validation 2 — Client ad account access:\*\*  
\`\`\`bash  
AD\_ACCOUNT\_ID="act\_\[CLIENT\_AD\_ACCOUNT\]"  
curl \-s "https://graph.facebook.com/v22.0/${AD\_ACCOUNT\_ID}?fields=name,account\_status\&access\_token=${TOKEN}" | python3 \-m json.tool  
\`\`\`  
\- ✅ Returns \`name\` \+ \`account\_status\` → pass  
\- ❌ Returns error 190/100/273 → \*\*HARD STOP\*\* → tell user: "El cliente no ha otorgado permiso ads\_read. No puedo generar un Sales Velocity Report sin datos de Meta Ads. Pídele que otorgue acceso."

\*\*Gate result:\*\*  
\- \*\*BOTH pass\*\* → proceed to STEP 1  
\- \*\*ANY fails\*\* → STOP immediately. Report to user what failed and what action is needed. Do NOT proceed to pipeline extraction, NotebookLM, or HTML generation.  
\- \*\*User says \`--force\` or explicitly overrides\*\* → proceed but add a visible ⚠️ banner in the report: "REPORTE SIN DATOS DE META ADS — Generado con \--force. Datos de ads NO disponibles."

\---

\#\#\# STEP 1: Extract Fresh Meta Ads Data (Campaign \+ Ad Level)  
// turbo

1\. \*\*Campaign-level data\*\* (7 days): name, status, spend, impressions, clicks, reach, frequency, leads, CPR, CTR  
2\. \*\*Ad-level data\*\* (7 days): name, status (ACTIVE/PAUSED), ad set, spend, clicks, reach, actions (complete\_registration)  
3\. \*\*Calculate per ad:\*\* registrations, CPR, status  
4\. \*\*For paused ads, determine reason:\*\*  
   \- "$X spent with 0 registrations"  
   \- "Good CTR but 0 conversions — hook doesn't close"  
   \- "Meta didn't distribute (\<50 impressions)"  
   \- "High CPR vs sibling ads"

\---

\#\#\# STEP 2: Extract GHL Pipeline Data & Correlate  
// turbo

\> \[\!CAUTION\]  
\> \*\*GHL API RULES — HARD-WON LEARNINGS (2026-03-17). NEVER DEVIATE.\*\*  
\> 1\. \*\*POST not GET\*\*: \`POST /opportunities/search\` — GET triggers Cloudflare 403/1010 blocks.  
\> 2\. \*\*Body params only\*\*: \`{"locationId": "..."}\` in JSON body. NO query params. camelCase only.  
\> 3\. \*\*NO pipelineId filter\*\*: PIT tokens cannot filter by pipeline. Pull ALL opps, then filter client-side by \`pipelineId\` field on each opp (matched via stage→pipeline mapping from \`/opportunities/pipelines\`).  
\> 4\. \*\*HTTP 201 \= success\*\*: GHL returns 201 (not 200\) for search results. Accept BOTH 200 and 201\.  
\> 5\. \*\*Use \`requests\` library\*\*: NOT \`urllib\` — \`urllib\` gets blocked by Cloudflare's user-agent checks.  
\> 6\. \*\*Pagination\*\*: \`{"page": N, "limit": 100}\` — stop when \`len(results) \< 100\`.  
\> 7\. \*\*Stage map first\*\*: Always call \`GET /opportunities/pipelines?locationId=...\` FIRST to build stage\_id→name and stage\_id→pipeline\_id maps.  
\> 8\. \*\*Resolve seller IDs\*\*: \`GET /users/{userId}\` returns name, email. Map \`assignedTo\` IDs to real names for commission calculations.

\*\*Extraction steps (use \`extract\_client\_data.py\` or replicate this exact pattern):\*\*

1\. \*\*Single-pass fetch\*\*: Call \`\_ghl\_fetch\_all\_opportunities()\` ONCE → returns ALL opps across all pipelines  
2\. \*\*Client-side filter\*\*: Split by \`pipelineId\` to get per-pipeline data  
3\. \*\*Identify ventas\*\*: Look for stage names containing "Venta", "comprar", "Won", "Cerrado" (case-insensitive), excluding "No Venta", "No Califica", "Casi"  
4\. \*\*Identify casi ventas\*\*: Stage names containing "Casi Venta", "Seguimiento"  
5\. \*\*Extract monetary values\*\*: \`opp.monetaryValue\` — flag any venta with $0 as "pendiente de valor"  
6\. \*\*Resolve sellers\*\*: Map \`assignedTo\` user IDs to names via \`/users/{id}\` endpoint

\---

\#\#\# STEP 3: Consult NotebookLM  
// turbo

\> \[\!CAUTION\]  
\> MANDATORY — NEVER SKIP. HARD STOP if auth fails.

1\. \*\*Query 1 — Benchmarks \+ Comparison\*\* (include previous week data if available)  
2\. \*\*Query 2 — Actions with pipeline context\*\* (include qualification rates, booking rate)

\---

\#\#\# STEP 4: Build HTML Report  
// turbo

File: \`07\_meta\_reviews/sv\_report\_\[YYYY-MM-DD\].html\`

\*\*7 Required Sections:\*\*

\#\#\#\# Header  
\- "SALES VELOCITY REPORT — \[CLIENT\]"  
\- Report \# badge, date, "Sales Velocity x \[Brand\]"

\#\#\#\# 01 — Veredicto Ejecutivo  
Traffic light (green/yellow/red) \+ 1-paragraph summary

\#\#\#\# 02 — KPIs Consolidados (WITH DELTAS)  
Each KPI card shows: Current | Previous | Delta (arrow \+ color) | Benchmark | Status  
\- Cost metrics (CPR, CPC, CPM): decrease \= green, increase \= red  
\- Performance metrics (CTR, leads, qualified%): increase \= green, decrease \= red  
\- If no previous: show "BASELINE" tag

\#\#\#\# 03 — Desglose por Campana  
Per campaign: header with totals, ad table (active \+ paused with reasons)  
Winner callout (green), paused explanation (red)  
If previous: delta column per campaign

\#\#\#\# 04 — Correlacion Meta → Pipeline GHL  
Quality cards (qualified/pending/disqualified/lost) with deltas vs previous  
Funnel bar chart by stage  
If previous: show quality delta percentages

\#\#\#\# 05 — Detalle de Leads  
Table: name, GHL stage, date, campaign (UTM), status emoji  
Color-coded. If previous: badge "NEW" for leads not in last report

\#\#\#\# 06 — Comparacion vs Reporte Anterior  
\*\*If baseline:\*\* "Este es el primer Sales Velocity Report" badge  
\*\*If previous exists:\*\*  
\- Metric comparison table (previous vs current vs change vs trend)  
\- Actions follow-up: which were implemented, results, pending  
\- Narrative: "La semana pasada se recomendo X. Se implemento Y. Resultado: Z."

\#\#\#\# 07 — Acciones Prioritarias (Detailed)  
Each action (max 5-7) includes:  
\- Priority: P1 URGENTE / P2 ALTO / P3 MEDIO  
\- Title  
\- Responsible: name \+ role  
\- Deadline: specific date  
\- Success metric: measurable KPI  
\- Effort: time estimate  
\- Expected impact  
\- Steps: 3-5 numbered instructions

\#\#\#\# Footer \+ JSON Data Block  
\- \`\<script type="application/json" id="review-data"\>\` with all metrics for future parsing

\---

\#\#\# STEP 5: Deploy & Distribute

1\. Save locally in \`07\_meta\_reviews/\`  
2\. Deploy to GitHub Pages (\`05\_deploy/\`)  
3\. Create Notion task with actions and responsibles  
4\. Update DELIVERABLES.md

\---

\#\#\# STEP 6: Verify  
// turbo

1\. Open GitHub Pages URL — verify all 7 sections render  
2\. Confirm JSON data block parseable  
3\. Verify Notion task created  
4\. Confirm DELIVERABLES.md updated

\---

\#\# Delta Calculation Reference

\`\`\`python  
def calc\_delta(current, previous, metric\_type="cost"):  
    if previous \== 0 or previous is None:  
        return (None, "", "neutral")  
    delta\_pct \= ((current \- previous) / previous) \* 100  
    if metric\_type \== "cost":  
        color \= "green" if delta\_pct \< 0 else "red"  
        arrow \= "down" if delta\_pct \< 0 else "up"  
    else:  
        color \= "green" if delta\_pct \> 0 else "red"  
        arrow \= "up" if delta\_pct \> 0 else "down"  
    return (delta\_pct, arrow, color)  
\`\`\`

| Cost Metrics (lower=better) | Performance Metrics (higher=better) |  
|---|---|  
| CPR, CPC, CPM | CTR, Leads, ROAS, Qualified%, Booking Rate |

\---

\#\# Cadence  
\- \*\*Primary:\*\* Thursday-Friday after 7AM auto-extraction  
\- \*\*On-demand:\*\* Before client meetings  
\- \*\*Alert (future):\*\* CPR increase \>30% → auto-flag

\#\# Immutability Rules  
1\. NEVER overwrite existing \`sv\_report\_\[DATE\].html\`  
2\. Each report is permanent  
3\. \`latest.html\` is the only overwritten file  
4\. Previous JSON data: read only

\#\# Notes  
\- NotebookLM notebook has 51 sources (benchmarks, Andromeda, best practices)  
\- Old \`/meta-ads-review\` files recognized for comparison during migration  
\- Report answers: "What happened, how does it compare, what to do, who does it, by when"  
