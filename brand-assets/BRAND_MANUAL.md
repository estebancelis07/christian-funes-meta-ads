# 📘 Manual de Marca — Christian Funes

---

## 🎯 Identidad de Marca

| Elemento | Valor |
|----------|-------|
| **Nombre** | Christian Funes |
| **Tagline** | *"Aprueba primero, compra después."* |
| **Industria** | Mortgage Broker · Financiamiento Hipotecario · Real Estate |
| **Personalidad** | Directo, confiable, resolutivo, transparente, experto |
| **Handle** | @christianfunes |
| **Web** | [Por definir] |
| **Email** | [Por definir] |
| **Ubicación** | Florida, Estados Unidos |

### Pilares de Marca

| Pilar | Esencia |
|-------|---------|
| **Certeza** | Aprobación blindada antes de ver casas. No promesas vacías — diagnóstico real en 15 minutos. |
| **Velocidad** | Cierre de casa en 21-45 días. Aprobación en 24-48 horas. Acceso directo a lenders. |
| **Acceso** | Programas alternativos para hispanos, Self-Employed, ITIN. Lo que importa es tu flujo de dinero real, no tus taxes. |

---

## 🎨 Paleta de Colores

### Colores Primarios

| Color | Hex | RGB | Uso |
|-------|-----|-----|-----|
| **Navy Profundo** | `#0F1B3D` | 15, 27, 61 | Fondos hero, secciones oscuras, texto principal |
| **Navy Claro** | `#1E3A8A` | 30, 58, 138 | Fondos secundarios, gradientes, avatares |
| **Blanco** | `#FFFFFF` | 255, 255, 255 | Fondos claros, texto sobre fondos oscuros |

### Colores Secundarios

| Color | Hex | Uso |
|-------|-----|-----|
| **Gray 50** | `#F8FAFC` | Fondo de secciones alternas (Social Proof) |
| **Gray 100** | `#F1F5F9` | Fondos de elementos UI (FAQ icons) |
| **Gray 200** | `#E2E8F0` | Bordes de separación (FAQ dividers) |
| **Gray 300** | `#CBD5E1` | Texto subtítulos sobre fondos oscuros |
| **Gray 400** | `#94A3B8` | Microcopy, trust items, texto terciario |
| **Gray 500** | `#64748B` | Labels, texto secundario en fondos claros |
| **Gray 600** | `#475569` | Respuestas FAQ, texto cuerpo secundario |
| **Gray 700** | `#334155` | Quotes de testimonios |
| **Gray 800** | `#1E293B` | Texto principal en secciones claras |

### Color de Acento — Dorado (Gold)

| Color | Hex | RGB | Uso |
|-------|-----|-----|-----|
| **Gold** | `#F59E0B` | 245, 158, 11 | Acento principal: CTAs, headlines destacados, eyebrow badges, bordes testimonios |
| **Gold Dark** | `#D97706` | 217, 119, 6 | Gradientes de botones, hover states, section labels |
| **Gold Glow** | `rgba(245,158,11,0.15)` | — | Glow de inputs al focus, fondos de radio seleccionados, efectos de luz |

### Color Secundario de Acento — Azul

| Color | Hex | RGB | Uso |
|-------|-----|-----|-----|
| **Blue** | `#2563EB` | 37, 99, 235 | Enlaces, hover de preguntas FAQ, elementos de acción secundarios |
| **Blue Light** | `#3B82F6` | 59, 130, 246 | Gradientes secundarios, detalles de avatares |

### Colores Semánticos

| Color | Hex | Uso |
|-------|-----|-----|
| **Success** | `#10B981` | Resultados de testimonios, confirmaciones, checks |
| **Error** | `#EF4444` | Validación de formularios, estados de error |

### Colores de Superposición (Overlays)

| Overlay | Valor | Uso |
|---------|-------|-----|
| **Hero Overlay** | `linear-gradient(165deg, #0F1B3D 0%, #0A1128 60%, #0D1833 100%)` | Gradiente principal del hero |
| **Form Overlay** | `linear-gradient(165deg, #0F1B3D 0%, #0A1128 100%)` | Sección de formulario y cierre |
| **Sticky CTA** | `rgba(15, 27, 61, 0.95)` | Barra fija inferior (mobile) |
| **Footer** | `#060B1A` | Footer oscuro |
| **Glass Inputs** | `rgba(255, 255, 255, 0.05-0.08)` | Inputs y cards sobre fondos oscuros |

### Principio de Color

> **Autoridad con calidez.** La base de la marca es un Navy profundo que transmite confianza financiera y profesionalismo. El Gold aparece como acento estratégico (CTAs, badges, bordes) para evocar valor, urgencia y premium. El azul complementa como acento técnico. El Gold nunca domina — es el punto de acción que guía al usuario. Las secciones alternan entre Navy oscuro y fondos claros grises para crear ritmo visual.

---

## 🔤 Tipografía

### Fuentes de la Marca

**Montserrat** (Headlines) — [Google Fonts](https://fonts.google.com/specimen/Montserrat)
**Inter** (Body) — [Google Fonts](https://fonts.google.com/specimen/Inter)

```css
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@600;700;800&family=Inter:wght@400;500;600&display=swap');

/* Headlines */
font-family: 'Montserrat', system-ui, -apple-system, sans-serif;

/* Cuerpo */
font-family: 'Inter', system-ui, -apple-system, sans-serif;
```

### Escala Tipográfica

| Peso | Valor | Fuente | Uso |
|------|-------|--------|-----|
| Regular | `font-weight: 400` | Inter | Cuerpo de texto, subheadlines |
| Medium | `font-weight: 500` | Inter | Texto destacado, trust items |
| SemiBold | `font-weight: 600` | Inter / Montserrat | Labels, form labels, nombres de testimonios |
| Bold | `font-weight: 700` | Montserrat | Títulos de sección (h2), CTAs |
| Extra Bold | `font-weight: 800` | Montserrat | Hero title (h1), closing h2, stats numbers |

### Tamaños (Desktop → Mobile)

| Elemento | Mobile (base) | Tablet (≥768px) | Desktop (≥1024px) |
|----------|---------------|------------------|--------------------|
| **Hero Title (h1)** | 32px | 48px | 56px |
| **Section Titles (h2)** | 26px | 36px | 36px |
| **Closing h2** | 28px | 40px | 40px |
| **Subheadline** | 17px | 19px | 19px |
| **Body Text** | 16px | 16px | 16px |
| **CTA Buttons** | 18px | 20px | 20px |
| **Testimonial Quote** | 16px | 16px | 16px |
| **Eyebrow Badge** | 11px | 11px | 11px |
| **Labels / Microcopy** | 12-13px | 12-13px | 12-13px |
| **Stats Numbers** | 28px | 36px | 36px |

### Atributos Tipográficos Clave

```css
/* Hero Title — bold, tight leading */
font-weight: 800;
line-height: 1.15;

/* Body Text — generous spacing */
line-height: 1.6;

/* Eyebrow Badge — uppercase, tracking abierto */
letter-spacing: 1.5px;
text-transform: uppercase;
font-weight: 600;

/* Section Labels — uppercase, wide tracking */
letter-spacing: 2px;
text-transform: uppercase;
font-weight: 600;

/* CTA Buttons — slight tracking */
letter-spacing: 0.3px;
font-weight: 700;
```

### Fuente Alternativa

`system-ui, -apple-system, sans-serif` (fallback automático)

---

## 📐 Espaciado y Layout

| Principio | Valor |
|-----------|-------|
| **Max-width contenido** | 720px (mobile-first VSL) |
| **Max-width (desktop)** | 780px |
| **Padding lateral (mobile)** | 20px |
| **Padding lateral (desktop)** | 32px |
| **Sección padding (mobile)** | 60px top/bottom |
| **Sección padding (desktop)** | 80px top/bottom |
| **Border-radius SM** | 8px |
| **Border-radius MD** | 12px |
| **Border-radius LG** | 16px |
| **Border-radius XL** | 20px |

---

## 🧩 Componentes de Diseño

### 1. Botón CTA Principal (Gold)

```css
.cta-btn {
    display: block;
    width: 100%;
    padding: 18px 24px;
    background: linear-gradient(135deg, #F59E0B 0%, #D97706 100%);
    color: #0F1B3D;
    font-family: 'Montserrat', sans-serif;
    font-size: 18px;
    font-weight: 700;
    text-align: center;
    text-decoration: none;
    border-radius: 12px;
    border: none;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 4px 20px rgba(245, 158, 11, 0.35);
    letter-spacing: 0.3px;
}

.cta-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 30px rgba(245, 158, 11, 0.5);
}

.cta-btn:active {
    transform: translateY(0);
    box-shadow: 0 2px 10px rgba(245, 158, 11, 0.3);
}

/* Animación de pulso sutil */
@keyframes subtlePulse {
    0%, 100% { box-shadow: 0 4px 20px rgba(245, 158, 11, 0.35); }
    50% { box-shadow: 0 4px 30px rgba(245, 158, 11, 0.55); }
}

.cta-pulse {
    animation: subtlePulse 2.5s ease-in-out infinite;
}
```

### 2. Eyebrow Badge

```css
.eyebrow {
    display: inline-block;
    background: rgba(245, 158, 11, 0.12);
    border: 1px solid rgba(245, 158, 11, 0.3);
    color: #F59E0B;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    padding: 6px 16px;
    border-radius: 100px;
}
```

### 3. Tarjetas de Testimonios

```css
.testimonial-card {
    background: #FFFFFF;
    border-radius: 16px;
    padding: 28px 24px;
    border-left: 4px solid #F59E0B;
    box-shadow: 0 2px 12px rgba(0, 0, 0, 0.06);
    transition: transform 0.2s, box-shadow 0.2s;
}

.testimonial-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 24px rgba(0, 0, 0, 0.1);
}
```

### 4. Stats Bar

```css
.stat-item {
    text-align: center;
    padding: 20px 8px;
    background: #FFFFFF;
    border-radius: 12px;
    box-shadow: 0 1px 4px rgba(0, 0, 0, 0.06);
}

.stat-number {
    font-family: 'Montserrat', sans-serif;
    font-size: 28px;  /* Mobile */
    font-weight: 800;
    color: #0F1B3D;
}
```

### 5. Form Card (Glassmorphism)

```css
.form-card {
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 20px;
    padding: 32px 24px;
    backdrop-filter: blur(10px);
}

.form-input {
    width: 100%;
    padding: 14px 16px;
    background: rgba(255, 255, 255, 0.08);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 8px;
    color: #FFFFFF;
    font-size: 16px;
}

.form-input:focus {
    border-color: #F59E0B;
    box-shadow: 0 0 0 3px rgba(245, 158, 11, 0.15);
}
```

### 6. FAQ Accordion

```css
.faq-question {
    font-size: 16px;
    font-weight: 600;
    color: #0F1B3D;
}

.faq-question:hover {
    color: #2563EB;
}

.faq-icon {
    width: 28px;
    height: 28px;
    border-radius: 50%;
    background: #F1F5F9;
}

.faq-item.active .faq-icon {
    transform: rotate(45deg);
    background: #0F1B3D;
    color: #FFFFFF;
}
```

---

## 🖼️ Dirección de Fotografía

| Atributo | Descripción |
|----------|-------------|
| **Iluminación** | Profesional, limpia, tonos neutros-cálidos |
| **Mood** | Confiable, accesible, profesional pero cercano |
| **Composición** | Christian como figura central; fondos minimalistas o contexto de bienes raíces |
| **Color fotográfico** | Tonos neutros que armonicen con la paleta Navy/Gold |
| **Pose/Estilo** | Frontal, contacto visual directo, expresión de confianza y seguridad |

### Tratamiento de Imágenes en Web

```css
/* Hero image container */
.hero-image-wrapper {
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5),
                0 0 0 1px rgba(245, 158, 11, 0.15);
}

/* Imagen: contain, no crop */
.hero-image-wrapper img {
    width: 100%;
    height: auto;
    object-fit: contain;
}
```

---

## ✍️ Tono de Voz

### Características

| Atributo | Descripción |
|----------|-------------|
| **Idioma** | Español (audiencia hispana en Estados Unidos) |
| **Tono** | Directo, honesto, resolutivo — como un aliado experto |
| **Perspectiva** | Primera persona plural ("Nosotros tenemos el dinero") y segunda persona directa ("Tú") |
| **Energía** | Confiada, urgente pero no agresiva, empoderada |

### Frases Clave de la Marca

- *"Aprueba primero, compra después."*
- *"El Realtor solo tiene las llaves. Nosotros tenemos el dinero."*
- *"La diferencia entre 'creer' y 'saber' que puedes comprar."*
- *"No compres una promesa. Compra una casa."*
- *"Lo que importa es tu flujo de dinero real, no tus taxes."*
- *"Obtén tu Poder de Compra Real en 15 Minutos."*

### Vocabulario de Marca

| Sí usar ✅ | No usar ❌ |
|------------|-----------|
| Certeza, Poder de Compra, Aprobación Blindada | "Le ayudamos con su hipoteca" (genérico) |
| Diagnóstico, Cierre Rápido, Direct Lender | "Tal vez califiques", "puede que funcione" |
| Cash-like Buyer, Comprador Serio | "Precio accesible", "oferta limitada" |
| Sin BS, Sin compromiso, Sin costo | Jerga corporativa, disclaimers excesivos |
| Flujo de dinero real, Programas alternativos | "Sujeto a aprobación crediticia" (como CTA) |

### Principios de Comunicación

1. **Directo y sin rodeos**: Cada palabra tiene un propósito. Nada de relleno.
2. **Honesto sobre lo difícil**: Si no calificas, te lo decimos y te explicamos qué hacer.
3. **Contraste con la industria**: Siempre comparar la forma "incorrecta" (Realtor primero) vs. la forma correcta (aprobación primero).
4. **Urgencia real**: Basada en hechos (80% de los tratos se caen, 15 minutos para cerrar diagnóstico).
5. **Empoderamiento del comprador**: El cliente pasa de víctima a comprador poderoso.

### Reglas de Escritura

- Oraciones cortas y punchy
- Voz activa SIEMPRE
- Usar números específicos: "200+ familias", "21-45 días", "15 minutos"
- Emojis estratégicos en digital: ⚡🏠🛡️🚀🏦✅
- Preguntas retóricas como hooks: "¿Por qué no debo ir primero con un Realtor?"
- "Sin costo · Sin compromiso · Sin BS" como tagline de acción

---

## 🎨 Design Tokens (CSS Variables)

```css
:root {
    /* ── Colores Primarios ── */
    --cf-navy: #0F1B3D;
    --cf-navy-light: #1E3A8A;
    --cf-white: #FFFFFF;

    /* ── Acento Gold ── */
    --cf-gold: #F59E0B;
    --cf-gold-dark: #D97706;
    --cf-gold-glow: rgba(245, 158, 11, 0.15);
    --cf-gold-gradient: linear-gradient(135deg, #F59E0B 0%, #D97706 100%);

    /* ── Acento Blue ── */
    --cf-blue: #2563EB;
    --cf-blue-light: #3B82F6;

    /* ── Grises ── */
    --cf-gray-50: #F8FAFC;
    --cf-gray-100: #F1F5F9;
    --cf-gray-200: #E2E8F0;
    --cf-gray-300: #CBD5E1;
    --cf-gray-400: #94A3B8;
    --cf-gray-500: #64748B;
    --cf-gray-600: #475569;
    --cf-gray-700: #334155;
    --cf-gray-800: #1E293B;

    /* ── Semánticos ── */
    --cf-success: #10B981;
    --cf-error: #EF4444;

    /* ── Overlays ── */
    --cf-overlay-hero: linear-gradient(165deg, #0F1B3D 0%, #0A1128 60%, #0D1833 100%);
    --cf-overlay-form: linear-gradient(165deg, #0F1B3D 0%, #0A1128 100%);
    --cf-overlay-sticky: rgba(15, 27, 61, 0.95);
    --cf-footer-bg: #060B1A;

    /* ── Tipografía ── */
    --cf-font-heading: 'Montserrat', system-ui, -apple-system, sans-serif;
    --cf-font-body: 'Inter', system-ui, -apple-system, sans-serif;

    /* ── Espaciado ── */
    --cf-section-py: 60px;
    --cf-section-py-desktop: 80px;
    --cf-container-px: 20px;
    --cf-container-px-desktop: 32px;
    --cf-max-width: 720px;
    --cf-max-width-desktop: 780px;

    /* ── Radii ── */
    --cf-radius-sm: 8px;
    --cf-radius-md: 12px;
    --cf-radius-lg: 16px;
    --cf-radius-xl: 20px;

    /* ── Sombras ── */
    --cf-shadow-card: 0 2px 12px rgba(0, 0, 0, 0.06);
    --cf-shadow-card-hover: 0 6px 24px rgba(0, 0, 0, 0.1);
    --cf-shadow-cta: 0 4px 20px rgba(245, 158, 11, 0.35);
    --cf-shadow-cta-hover: 0 8px 30px rgba(245, 158, 11, 0.5);
    --cf-shadow-hero-image: 0 20px 60px rgba(0, 0, 0, 0.5), 0 0 0 1px rgba(245, 158, 11, 0.15);

    /* ── Transiciones ── */
    --cf-transition: all 0.2s ease;
    --cf-transition-slow: all 0.3s ease;
}
```

---

## 📐 Estructura de Página (VSL Landing)

```
┌─────────────────────────────────┐
│     🏠 Eyebrow Badge           │  ← Gold pill badge
│                                 │
│   Deja de Ver Casas que         │  ← Hero h1, Extra Bold
│   NO Puedes Comprar.            │     "NO" en Gold
│   Obtén tu Poder de Compra Real │     Subrayado gold
│                                 │
│   ┌───────────────────┐         │  ← Hero Image (contain)
│   │  Christian Funes  │         │     rounded, gold border glow
│   └───────────────────┘         │
│                                 │
│   🛡️ Aprobación  🚀 21-45  🏦  │  ← Trust Bar
│                                 │
│   ⚡ QUIERO MI DIAGNÓSTICO     │  ← CTA Gold gradient + pulse
│   ✅ Sin costo · Sin compromiso │
└─────────────────────────────────┘
┌─────────────────────────────────┐
│   Familias que Compraron        │  ← Social Proof section
│   con Certeza                   │     bg: gray-50
│                                 │
│   ┌─ FM ─────────────────┐     │  ← Testimonial cards
│   │ "Perdí 3 meses..."   │     │     border-left: gold
│   │  ✓ Cerró en 30 días  │     │
│   └──────────────────────┘     │
│                                 │
│   ┌────┐ ┌────┐ ┌────┐        │  ← Stats bar
│   │200+│ │ 8  │ │ 45 │        │     font-weight: 800
│   └────┘ └────┘ └────┘        │
└─────────────────────────────────┘
┌─────────────────────────────────┐
│   ⚡ Tu Primer Paso            │  ← Form Section
│   Agenda tu Diagnóstico         │     bg: navy gradient
│                                 │
│   ┌──────────────────────┐     │  ← Glassmorphism card
│   │ Nombre              │     │     backdrop-filter: blur
│   │ Teléfono (WhatsApp) │     │
│   │ ¿Realtor? [Sí] [No] │     │
│   │ Presupuesto ▾       │     │
│   │ Mudanza [ASAP] [3-6]│     │
│   │                      │     │
│   │ ⚡ DIAGNÓSTICO GRATIS│     │
│   └──────────────────────┘     │
└─────────────────────────────────┘
┌─────────────────────────────────┐
│   Preguntas Frecuentes          │  ← FAQ Accordion
│                                 │     bg: white
│   ▶ ¿Por qué no Realtor?  [+]  │
│   ▶ ¿Cuánto cuesta?       [+]  │
│   ▶ ¿Mi propio Realtor?   [+]  │
│   ▶ ¿Cuánto tarda?        [+]  │
│   ▶ ¿Self-Employed/ITIN?  [+]  │
└─────────────────────────────────┘
┌─────────────────────────────────┐
│   No Compres una Promesa.       │  ← Closing CTA
│   Compra una Casa.              │     bg: navy gradient
│                                 │
│   ⚡ AGENDA TU DIAGNÓSTICO     │
│   🛡️  🚀  🏦                   │  ← Trust badges
└─────────────────────────────────┘
┌─────────────────────────────────┐
│   © 2026 Christian Funes        │  ← Footer
│   Privacidad · Términos         │     bg: #060B1A
└─────────────────────────────────┘
```

---

## ❌ Usos Incorrectos

| No hacer | Por qué |
|----------|---------|
| 🚫 Usar otro acento que no sea Gold | Solo Gold (#F59E0B) y su gradiente están autorizados como acento de acción |
| 🚫 Usar Gold como fondo dominante | Es un acento de acción (CTAs, badges, bordes) — no un color de fondo |
| 🚫 Tipografías no autorizadas | Solo Montserrat (headlines) e Inter (body) |
| 🚫 Fondos planos sin gradiente en secciones hero | Las secciones oscuras usan gradientes Navy 165deg |
| 🚫 Imágenes sin border-radius y shadow | Las imágenes hero llevan border-radius: 16px + shadow con glow gold |
| 🚫 CTAs sin animación de pulso | Los botones principales llevan `subtlePulse` para guiar la atención |
| 🚫 Texto en español formal/corporativo | El tono es directo, cercano, conversacional |
| 🚫 Promesas vagas ("te podemos ayudar") | Números específicos: 15 min, 200+ familias, 21-45 días |
| 🚫 Layout más ancho de 780px | El diseño es mobile-first VSL, contenido estrecho para alta conversión |

---

## 📥 Archivos de Referencia

| Archivo | Ubicación |
|---------|-----------|
| Hero Image | `christian_funes_vsl/Gemini_Generated_Image_jbogznjbogznjbog.jpeg` |
| Hero PNG | `christian_funes_vsl/christian-hero.png` |
| VSL Landing Page | `christian_funes_vsl/index.html` |
| GHL Snippet | `christian_funes_vsl/ghl-snippet.html` |
| GHL Implementation Guide | `christian_funes_vsl/ghl-implementation-guide.md` |

---

## 📊 Datos Clave de la Marca

| Dato | Valor |
|------|-------|
| **Familias ayudadas** | 200+ |
| **Años de experiencia** | 8 |
| **Tiempo de cierre** | 21-45 días |
| **Diagnóstico** | 15 minutos, gratuito |
| **Aprobación** | 24-48 horas |
| **Mercado** | Hispanos en Florida, USA |
| **Especialidades** | Self-Employed, ITIN, Programas alternativos |
| **Ventaja competitiva** | Direct Lender Access, tasas preferenciales, velocidad |

---

*Manual de Marca v1.0 — Christian Funes — Febrero 2026*
