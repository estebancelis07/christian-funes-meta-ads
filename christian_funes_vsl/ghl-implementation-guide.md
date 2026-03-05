# GHL Implementation Guide — Christian Funes VSL Landing Page

> **Deliverables included:**
> - `index.html` — Standalone preview (open locally to test)
> - `ghl-snippet.html` — Copy/paste into GHL Custom HTML element
> - This guide

---

## 1. Pre-Flight Checklist

Before pasting anything into GHL, gather these values:

| Placeholder | Where to find it | Example |
|---|---|---|
| `[YOUR_VIMEO_OR_YOUTUBE_EMBED_URL]` | Vimeo/YouTube → Share → Embed | `https://player.vimeo.com/video/123456` |
| `[YOUR_GHL_CALENDAR_URL]` | GHL → Calendars → Embed Link | `https://app.gohighlevel.com/widget/booking/abc123` |
| `[YOUR_GHL_WEBHOOK_URL]` | GHL → Automations → Webhook trigger URL | `https://services.leadconnectorhq.com/hooks/...` |
| `[YOUR_GA_MEASUREMENT_ID]` | Google Analytics → Admin → Data Streams | `G-XXXXXXXXXX` |
| `[YOUR_FB_PIXEL_ID]` | Meta Events Manager → Data Sources | `123456789012345` |
| `[YOUR_CANONICAL_URL]` | The final live URL of this page | `https://christianfunes.com/vsl` |
| `[YOUR_OG_IMAGE_URL]` | Hosted OG image (1200×630px) | `https://cdn.example.com/cf-og.jpg` |
| `[YOUR_PRIVACY_POLICY_URL]` | Privacy policy page URL | `https://christianfunes.com/privacy` |
| `[YOUR_TERMS_URL]` | Terms of service page URL | `https://christianfunes.com/terms` |

---

## 2. GHL Page Setup

### Option A: Funnel Page (Recommended)

1. **GHL → Sites → Funnels → + New Funnel**
2. Name: `Christian Funes VSL`
3. Add a **new step** → Name: `VSL Landing`
4. Choose **Blank Template**
5. In the editor, add a **Custom HTML** element (full-width)
6. Paste the entire contents of `ghl-snippet.html` into it
7. Save & publish

### Option B: Standalone Website Page

1. **GHL → Sites → Websites → [Your Site]**
2. Add new page → Name: `VSL`
3. Add a **Custom HTML** element (full-width row)
4. Paste `ghl-snippet.html` contents
5. Save & publish

> [!IMPORTANT]
> Use a **full-width section** with **0 padding** so the snippet controls all spacing.

---

## 3. Replace All Placeholders

Open `ghl-snippet.html` in a text editor (VS Code, Sublime, etc.) and **Find & Replace** each placeholder from the table in Step 1.

### Critical replacements:

```
Find: [YOUR_VIMEO_OR_YOUTUBE_EMBED_URL]
Replace: (your actual embed URL)

Find: [YOUR_GA_MEASUREMENT_ID]
Replace: (your GA4 ID)

Find: [YOUR_FB_PIXEL_ID]
Replace: (your Pixel ID)
```

After replacing, paste the updated HTML into GHL.

---

## 4. Form Submission Setup

The form has two integration options. Choose ONE:

### Option A: Redirect to GHL Calendar (Recommended for High-Ticket)

In the snippet's `<script>` section, find the form submission handler and uncomment the calendar redirect:

```javascript
// OPTION A — Redirect to GHL calendar
window.location.href = '[YOUR_GHL_CALENDAR_URL]'
  + '?name=' + encodeURIComponent(nombre)
  + '&phone=' + encodeURIComponent(telefono);
```

Remove or comment out the `alert()` placeholder.

### Option B: Submit to GHL Webhook

Uncomment the webhook fetch block:

```javascript
// OPTION B — Send to GHL webhook
fetch('[YOUR_GHL_WEBHOOK_URL]', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    nombre: nombre,
    telefono: telefono,
    tiene_realtor: tieneRealtor,
    presupuesto: presupuesto,
    cuando_mudarse: cuando
  })
});
```

### GHL Automation Setup (for Option B):

1. **GHL → Automations → + New Workflow**
2. Trigger: **Inbound Webhook**
3. Copy the webhook URL → replace `[YOUR_GHL_WEBHOOK_URL]` in the snippet
4. Add actions:
   - **Create/Update Contact** (map `nombre` → Name, `telefono` → Phone)
   - **Add Tag** → `vsl-christian-funes`
   - **Send Email** → Confirmation template
   - **Add to Pipeline** (optional)

---

## 5. Tracking Setup

### Google Analytics 4

The GA script is already in the snippet. Just replace `[YOUR_GA_MEASUREMENT_ID]`.

To track form submissions as conversions:

1. GA4 → Admin → Events → Create Event
2. Event name: `generate_lead`
3. In GHL snippet, the form submission already fires `gtag('event', 'generate_lead')`

### Facebook Pixel

The Pixel base code is in the snippet. Replace `[YOUR_FB_PIXEL_ID]`.

Events already configured in the snippet:
- `PageView` — fires on load
- `Lead` — fires on form submission

To verify: Use [Facebook Pixel Helper](https://chrome.google.com/webstore/detail/facebook-pixel-helper/fdgfkebogiimcoedlicjlajpkdmockpc) Chrome extension.

---

## 6. Mobile Testing Checklist

After publishing, test on real devices:

- [ ] Hero headline readable without scrolling on iPhone SE
- [ ] VSL video responsive (16:9 aspect ratio maintained)
- [ ] Form fields easy to tap (44px+ touch targets)
- [ ] FAQ accordion opens/closes smoothly
- [ ] Sticky bottom CTA visible and tappable
- [ ] Form submission works (calendar redirect or webhook)
- [ ] Page loads in < 3 seconds on 4G
- [ ] No horizontal scroll on any device
- [ ] Legal links (privacy/terms) are clickable

### Test devices:
- iPhone 12/13/14 (Safari)
- Samsung Galaxy S21+ (Chrome)
- iPad (landscape + portrait)
- Desktop Chrome, Firefox, Safari

---

## 7. UTM Tracking for Ads

When running Facebook/Google Ads to this page, use UTM parameters:

```
https://[YOUR_DOMAIN]/vsl?utm_source=facebook&utm_medium=cpc&utm_campaign=vsl-christian-funes&utm_content=ad-v1
```

The landing page will pass UTMs through to the form submission automatically if using the webhook option.

---

## 8. Post-Launch Optimization

### Week 1:
- [ ] Verify form submissions are arriving in GHL CRM
- [ ] Check GA4 for `generate_lead` events
- [ ] Check FB Pixel for `Lead` events
- [ ] Review mobile heatmaps (Hotjar free tier)

### Week 2-4:
- [ ] A/B test headline variations
- [ ] Test different VSL lengths
- [ ] Optimize form fields (fewer = higher conversion)
- [ ] Review bounce rate (target < 60%)

---

## Troubleshooting

| Issue | Fix |
|---|---|
| Styles look broken in GHL | Ensure you're using a full-width section with 0 padding |
| Font not loading | Check that `@import` for Google Fonts is at the top of `<style>` |
| Form not submitting | Check browser console (F12) for JS errors |
| Video not showing | Verify embed URL works in an incognito tab |
| Sticky CTA overlaps content | Check `z-index` value (should be 9999) |
| GHL adds extra padding | Add `!important` to body/section padding overrides |
