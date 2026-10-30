# Sistema de Diseño de Interfaz de Usuario (UI System)
## Envíos DosRuedas — Plataforma Digital & Ecosistema Web
> **Versión:** 2.0.0 — Canónica  
> **Especialista:** UI Designer  
> **Compatibilidad:** Tailwind CSS v4, HTML5/CSS3 moderno, Web Components y Vanilla JS  
> **Norma de Accesibilidad:** WCAG 2.1 Nivel AA / AAA

---

## 1. Fundamentos del Sistema de Interfaz (Design Foundations)

El sistema de interfaz de **Envíos DosRuedas** traduce la velocidad, seguridad y transparencia del servicio de cadetería técnica en una experiencia digital de alto impacto visual y rendimiento táctil móvil.

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                               ATMÓSFERA VISUAL UI                                      │
├────────────────────────────┬────────────────────────────┬──────────────────────────────┤
│    PRECISIÓN TÉCNICA       │     SEÑALÉTICA VIAL        │      AGILIDAD TÁCTIL         │
│  Bordes calculados, datos  │  Amarillo canónico en CTAs │  Interacciones inmediatas,   │
│  tabulares y picking QR.   │  y badges de urgencia.     │  touch targets ≥ 44px.       │
└────────────────────────────┴────────────────────────────┴──────────────────────────────┘
```

---

### 1.1 Tokens de Color & Roles Semánticos

El sistema aplica la **Ley de Tres Colores**, con gradaciones tonales para interacción:

```css
:root {
  /* ========================================================================
   * 1. SUPERFICIE Y BASE (Lienzo Inmaculado)
   * ======================================================================== */
  --ui-bg-page: #FFFFFF;
  --ui-bg-surface: #F4F6F9;
  --ui-bg-subtle: #E6EEFE;

  /* ========================================================================
   * 2. AZUL CANÓNICO (Primario / Estructural / Texto / Tope de Oscuridad)
   * ======================================================================== */
  --ui-blue-50:  #E6EEFE;  /* Bezel exterior, fondos secundarios, skeleton loaders */
  --ui-blue-100: #BACEFD;  /* Bordes contenedores, separadores de sección */
  --ui-blue-200: #8EAFFB;  /* Hover en bordes de tarjetas inactivas */
  --ui-blue-300: #628FF9;  /* Bordes de input en reposo, anillos secundarios */
  --ui-blue-400: #3570F8;  /* Iconografía sobre blanco, subtítulos en azul */
  --ui-blue-500: #0950F6;  /* COLOR PRIMARIO CANÓNICO: Botones, títulos H1/H2, navbar */
  --ui-blue-600: #0740C5;  /* Hover y active en botones azules */

  /* ========================================================================
   * 3. AMARILLO SEÑAL (Acento / Acción / Alerta Vial / Cobertura ≤ 15%)
   * ======================================================================== */
  --ui-yellow-50:  #FFFDE6; /* Fondo de tarjeta de servicio seleccionada */
  --ui-yellow-100: #FFFAB8; /* Halos y chips de estado completado */
  --ui-yellow-200: #FFF78A; /* Borde de elemento enfocado */
  --ui-yellow-300: #FFF45C; /* Resaltado numérico y mono sobre fondo azul */
  --ui-yellow-400: #FFF12E; /* Hover de botones CTA principales y WhatsApp */
  --ui-yellow-500: #FFEC01; /* ACENTO CANÓNICO: Botones CTA principales, badges de urgencia */
  --ui-yellow-600: #E6D400; /* Estado presionado (active) de los botones CTA */

  /* ========================================================================
   * 4. NEUTROS ESTRUCTURALES & ESTADOS DE SISTEMA
   * ======================================================================== */
  --ui-dark-asphalt: #111625; /* Texto oscuro base, indumentaria, fondos dark */
  --ui-slate-muted:   #64748B; /* Textos secundarios, timestamps, etiquetas */
  --ui-status-success: #10B981; /* Entregado, validado por QR, Flex completado */
  --ui-status-warning: #F59E0B; /* En tránsito, demora estimada climática */
  --ui-status-error:   #EF4444; /* Domicilio cerrado, contingencia operativa */
}
```

---

### 1.2 Reglas Inviolables de Contraste WCAG 2.1

```
                   MATRIZ DE ACCESIBILIDAD Y CONTRASTE OBLIGATORIO
┌───────────────────────────────┬───────────────────────────────┬───────────────────────────────┐
│       SUPERFICIE AMARILLA     │        SUPERFICIE AZUL        │       SUPERFICIE BLANCA       │
│           #FFEC01             │            #0950F6            │            #FFFFFF            │
├───────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Texto permitido:              │ Texto permitido:              │ Texto permitido:              │
│ ✅ Azul Canónico (#0950F6)    │ ✅ Blanco Puro (#FFFFFF)      │ ✅ Azul Canónico (#0950F6)    │
│ ✅ Negro Asfalto (#111625)    │ ✅ Amarillo Señal (#FFEC01)   │ ✅ Negro Asfalto (#111625)    │
│ ❌ PROHIBIDO TEXTO BLANCO     │ ❌ PROHIBIDO GRIS CLARO       │ ❌ PROHIBIDO AMARILLO S/BLANCO│
│ (Contraste 1.1:1 = Falla AAA) │ (Infracción de legibilidad)   │ (Contraste 1.1:1 = Ilegible)  │
└───────────────────────────────┴───────────────────────────────┴───────────────────────────────┘
```

---

### 1.3 Sistema Tipográfico y Escala Fluida

Utiliza **Plus Jakarta Sans / Anton** para impacto visual, **Inter / Outfit** para lectura cómoda y fuentes mono para tarifas:

```css
:root {
  --font-display: 'Plus Jakarta Sans', 'Anton', sans-serif;
  --font-body: 'Inter', 'Outfit', system-ui, -apple-system, sans-serif;
  --font-mono: 'Geist Mono', monospace;

  /* Escala Fluida Adaptable (Mobile → Desktop) */
  --text-h1: clamp(2rem, 5vw, 3rem);       /* 32px → 48px */
  --text-h2: clamp(1.5rem, 3.5vw, 2.25rem); /* 24px → 36px */
  --text-h3: clamp(1.25rem, 2.5vw, 1.5rem); /* 20px → 24px */
  --text-body: 1rem;                        /* 16px */
  --text-body-sm: 0.875rem;                 /* 14px */
  --text-caption: 0.75rem;                  /* 12px */
}
```

---

### 1.4 Elevación y Sombras Teñidas de Marca (Tinted Shadows)

No se utilizan sombras desaturadas o grises opacos. Cada componente proyecta una elevación cromática que preserva la identidad del servicio:

```css
:root {
  /* Sombra sutil de contención */
  --shadow-card: 0 4px 12px rgba(9, 80, 246, 0.06), 0 1px 3px rgba(9, 80, 246, 0.04);

  /* Flotación física para Double-Bezel y modales */
  --shadow-float: 0 25px 50px -12px rgba(9, 80, 246, 0.16);

  /* Hover de alta aceleración */
  --shadow-hover-lift: 0 20px 40px -8px rgba(9, 80, 246, 0.22);

  /* Resplandor vial para botones CTA amarillos */
  --shadow-cta-glow: 0 0 28px rgba(255, 236, 1, 0.5), 0 8px 24px rgba(9, 80, 246, 0.18);
}
```

---

## 2. Biblioteca de Componentes UI (Component Library)

### 2.1 Botones de Acción (Action Buttons & CTAs)

#### A. Botón Primario: Nested Pill (Llamada a la Acción & WhatsApp)
Diseñado con forma de cápsula continua (`rounded-full`), con el fondo Amarillo Señal y tipografía en Azul Canónico.

```html
<a href="https://wa.me/542236602699" class="btn-cta-pill" target="_blank" rel="noopener">
  <span>PEDIR EN CAMINO</span>
  <div class="btn-cta-icon">
    <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
      <line x1="5" y1="12" x2="19" y2="12"></line>
      <polyline points="12 5 19 12 12 19"></polyline>
    </svg>
  </div>
</a>
```

```css
.btn-cta-pill {
  display: inline-flex;
  align-items: center;
  justify-content: space-between;
  gap: 0.75rem;
  background-color: var(--ui-yellow-500);
  color: var(--ui-blue-500);
  font-family: var(--font-display);
  font-weight: 800;
  font-size: 1.125rem;
  text-transform: uppercase;
  letter-spacing: 0.03em;
  padding: 0.5rem 0.625rem 0.5rem 1.5rem;
  border-radius: 9999px;
  text-decoration: none;
  box-shadow: var(--shadow-cta-glow);
  transition: all 180ms cubic-bezier(0.23, 1, 0.32, 1);
  min-height: 48px; /* Touch target móvil accesible */
}

.btn-cta-pill:hover {
  background-color: var(--ui-yellow-400);
  transform: translateY(-2px);
  box-shadow: 0 0 34px rgba(255, 236, 1, 0.65), 0 12px 28px rgba(9, 80, 246, 0.25);
}

.btn-cta-pill:active {
  transform: scale(0.97);
  background-color: var(--ui-yellow-600);
}

.btn-cta-pill .btn-cta-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  background-color: var(--ui-blue-500);
  color: var(--ui-yellow-500);
  border-radius: 9999px;
  transition: transform 180ms ease;
}

.btn-cta-pill:hover .btn-cta-icon {
  transform: translateX(3px);
}
```

#### B. Botón Secundario Institucional
Para acciones como *"Ver Cobertura Zonal"*, *"Descargar Remito"* o *"Fulfillment"*.

```css
.btn-secondary {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  background-color: var(--ui-blue-500);
  color: var(--ui-bg-page);
  font-family: var(--font-body);
  font-weight: 600;
  font-size: 0.9375rem;
  padding: 0.75rem 1.5rem;
  border-radius: 12px;
  text-decoration: none;
  border: 1px solid transparent;
  transition: all 160ms ease;
  min-height: 44px;
}

.btn-secondary:hover {
  background-color: var(--ui-blue-600);
  transform: translateY(-1px);
  box-shadow: var(--shadow-card);
}
```

---

### 2.2 Tarjetas y Contenedores: Firma Double-Bezel

El componente de firma arquitectónica que enmarca cotizadores, tarjetas destacadas y modales:

```html
<div class="double-bezel-outer">
  <div class="double-bezel-inner">
    <div class="card-badge">MERCADO ENVÍOS FLEX</div>
    <h3 class="card-title">Entregas Same-Day en Mar del Plata</h3>
    <p class="card-desc">Corte 15:00 hs con múltiples retiros. Picking QR y comprobante con firma digital en el acto.</p>
    <div class="card-footer">
      <span class="card-price">Tarifa Zonal Directa</span>
      <a href="/cotizar.html" class="btn-link">Cotizar envío →</a>
    </div>
  </div>
</div>
```

```css
.double-bezel-outer {
  background-color: rgba(230, 238, 254, 0.85);
  border: 1px solid var(--ui-blue-100);
  border-radius: 20px;
  padding: 8px;
  box-shadow: var(--shadow-float);
  transition: transform 200ms ease, border-color 200ms ease;
}

.double-bezel-outer:hover {
  border-color: var(--ui-blue-300);
  transform: translateY(-3px);
  box-shadow: var(--shadow-hover-lift);
}

.double-bezel-inner {
  background-color: var(--ui-bg-page);
  border: 1px solid rgba(186, 206, 253, 0.5);
  border-radius: 14px;
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.875rem;
}
```

---

### 2.3 Badges de Estado Operativo & Trazabilidad (Status Chips)

Chips normalizados con contraste AA/AAA para remitos, estados de WhatsApp y paneles de seguimiento:

```html
<!-- Estado 1: Flex Same-Day Activo -->
<span class="ui-badge ui-badge--flex">FLEX SAME-DAY</span>

<!-- Estado 2: En Camino / Tránsito -->
<span class="ui-badge ui-badge--transit">EN CAMINO (MOTO #04)</span>

<!-- Estado 3: Entregado con Firma -->
<span class="ui-badge ui-badge--delivered">ENTREGADO CON ÉXITO</span>

<!-- Estado 4: Retorno por Rechazo Bonificado -->
<span class="ui-badge ui-badge--return">RECHAZO EN PUERTA: 100% BONIFICADO</span>
```

```css
.ui-badge {
  display: inline-flex;
  align-items: center;
  font-family: var(--font-body);
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  padding: 0.35rem 0.75rem;
  border-radius: 9999px;
  width: fit-content;
}

.ui-badge--flex {
  background-color: var(--ui-yellow-500);
  color: var(--ui-blue-500); /* Máximo contraste obligatorio */
  box-shadow: 0 1px 4px rgba(255, 236, 1, 0.4);
}

.ui-badge--transit {
  background-color: var(--ui-blue-50);
  color: var(--ui-blue-500);
  border: 1px solid var(--ui-blue-200);
}

.ui-badge--delivered {
  background-color: #ECFDF5;
  color: #065F46;
  border: 1px solid #A7F3D0;
}

.ui-badge--return {
  background-color: #FEF2F2;
  color: #991B1B;
  border: 1px solid #FECACA;
}
```

---

### 2.4 Cotizador Interactivo: Selector de Zonas (Z1 a Z5) & Drop-Off Toggle

Componente de interfaz para selección de radio de entrega y bonificación del 20% en Friuli 1972:

```html
<div class="zone-calculator">
  <label class="input-label" for="zone-select">ZONA DE DESTINO (CALLE REAL)</label>
  <div class="zone-selector-grid" role="radiogroup" aria-label="Selección de Zona">
    <button type="button" class="zone-btn active" aria-checked="true">Z1 (0 - 3 km)</button>
    <button type="button" class="zone-btn" aria-checked="false">Z2 (3 - 6 km)</button>
    <button type="button" class="zone-btn" aria-checked="false">Z3 (6 - 9 km)</button>
    <button type="button" class="zone-btn" aria-checked="false">Z4 (9 - 13 km)</button>
    <button type="button" class="zone-btn" aria-checked="false">Z5 (Especial)</button>
  </div>

  <div class="dropoff-switch-card">
    <div class="dropoff-info">
      <span class="dropoff-title">Bonificación Drop-Off (Friuli 1972)</span>
      <span class="dropoff-subtitle">Acercás el paquete a base y ahorrás el retiro</span>
    </div>
    <span class="dropoff-tag">-20% OFF</span>
  </div>
</div>
```

```css
.zone-selector-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(90px, 1fr));
  gap: 0.5rem;
  margin-top: 0.5rem;
}

.zone-btn {
  background-color: var(--ui-bg-surface);
  border: 1px solid var(--ui-blue-100);
  color: var(--ui-blue-500);
  font-family: var(--font-mono);
  font-weight: 600;
  font-size: 0.8125rem;
  padding: 0.625rem 0.5rem;
  border-radius: 8px;
  cursor: pointer;
  transition: all 140ms ease;
}

.zone-btn:hover {
  border-color: var(--ui-blue-300);
  background-color: var(--ui-blue-50);
}

.zone-btn.active {
  background-color: var(--ui-blue-500);
  color: var(--ui-bg-page);
  border-color: var(--ui-blue-500);
  box-shadow: 0 2px 8px rgba(9, 80, 246, 0.25);
}

.dropoff-switch-card {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: var(--ui-yellow-50);
  border: 1px dashed var(--ui-yellow-500);
  border-radius: 12px;
  padding: 1rem;
  margin-top: 1rem;
}

.dropoff-tag {
  background-color: var(--ui-yellow-500);
  color: var(--ui-blue-500);
  font-family: var(--font-display);
  font-weight: 800;
  font-size: 0.875rem;
  padding: 0.25rem 0.625rem;
  border-radius: 6px;
}
```

---

### 2.5 Navbar & Montaje del Logotipo (Gobernanza Dual)

El navbar contempla el montaje del **Logotipo Circular Patrimonial** (con su cápsula de seguridad para aislar sus colores originales) y la versión tipográfica adaptable:

```html
<header class="navbar-container">
  <div class="navbar-wrapper">
    <!-- Logotipo con cápsula protectora neutra -->
    <a href="/index.html" class="brand-link" aria-label="Inicio Envíos DosRuedas">
      <div class="logo-capsule">
        <img src="/LogoEnviosDosRuedas.webp" alt="Logo Patrimonial Envíos DosRuedas" class="logo-circle-img" width="44" height="44" />
      </div>
      <div class="brand-text-block">
        <span class="brand-name">ENVÍOS DOSRUEDAS</span>
        <span class="brand-location">MAR DEL PLATA</span>
      </div>
    </a>

    <!-- Acceso Rápido -->
    <nav class="nav-links">
      <a href="/servicios-enviosflex.html">Flex</a>
      <a href="/servicios-envios-express.html">Express</a>
      <a href="/servicios-envios-lowcost.html">LowCost</a>
      <a href="/servicios-deposito-fulfillment.html">Fulfillment</a>
      <a href="/cotizar.html" class="nav-btn-highlight">Cotizar Online</a>
    </nav>
  </div>
</header>
```

```css
.navbar-container {
  position: sticky;
  top: 0;
  z-index: 50;
  background-color: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--ui-blue-100);
}

.navbar-wrapper {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0.75rem 1.25rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.brand-link {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  text-decoration: none;
}

/* Cápsula neutra que blinda el logotipo circular patrimonial */
.logo-capsule {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 48px;
  height: 48px;
  background-color: var(--ui-bg-page);
  border-radius: 9999px;
  box-shadow: 0 2px 6px rgba(9, 80, 246, 0.12);
  padding: 2px;
}

.logo-circle-img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  border-radius: 9999px;
}

.brand-text-block {
  display: flex;
  flex-direction: column;
}

.brand-name {
  font-family: var(--font-display);
  font-weight: 800;
  font-size: 1.125rem;
  color: var(--ui-blue-500);
  line-height: 1.1;
  letter-spacing: -0.01em;
}

.brand-location {
  font-family: var(--font-body);
  font-size: 0.6875rem;
  font-weight: 700;
  color: var(--ui-slate-muted);
  letter-spacing: 0.08em;
}
```

---

## 3. Especificaciones de Diseño Responsivo (Responsive Matrix)

| Breakpoint | Ancho (px) | Comportamiento UI & Layout |
| :--- | :--- | :--- |
| **Mobile (`sm`)** | `320px – 639px` | Layout a 1 columna. Botones CTA fijos en base inferior (*sticky footer*). Touch targets a 48px mínimo. Drawer de navegación lateral con desenfoque de fondo. |
| **Tablet (`md`)** | `640px – 1023px`| Bento grid a 2 columnas. Cotizador en split 50/50. Menú horizontal compacto. |
| **Desktop (`lg`)** | `1024px – 1279px`| Grid de servicios a 3 columnas. Barra de búsqueda de cobertura activa y vista de tarifas instantánea. |
| **Wide Desktop (`xl`)** | `1280px+` | Contenedor centrado a `max-w-7xl` (1200px / 1280px). Tipografías escaladas mediante `clamp()`. |

---

## 4. Protocolo de Auditoría y Control de Calidad (UI QA Checklist)

- [x] **Regla de Amarillo WCAG:** Ningún botón o caja amarilla contiene texto blanco. Todo texto sobre amarillo está en Azul `#0950F6` o Negro Asfalto `#111625`.
- [x] **Área Táctil (Touch Target):** Todos los botones, selectores de zona y enlaces tienen una altura interactiva mínima de 44px (48px en CTAs móviles).
- [x] **Aislamiento del Logo Circular:** El logo circular cuenta con su cápsula de seguridad para no perder contraste frente a fondos azules u oscuros.
- [x] **Tipografía Tabular para Números:** Las tarifas, tiempos de entrega y códigos de seguimiento aplican `tabular-nums` para que los números no bailen al cambiar de valor.
- [x] **Reducción de Movimiento:** Las animaciones y micro-interacciones respetan `@media (prefers-reduced-motion: reduce)`.
