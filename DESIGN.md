# Design System: Envíos DosRuedas
**Skill:** stitch-design-taste / taste-design  
**Versión:** 1.0.0 — Canónica  
**Ámbito:** Todas las páginas y componentes en `/pagina/`

---

## Configuration — Dial Settings

| Dial | Level | Description |
| :--- | :---: | :--- |
| **Creativity** | `8` | Expresivo y enérgico: tipografía display condensada de alto impacto, contrastes viales audaces, insignias knockout y micro-interacciones táctiles. |
| **Density** | `6` | Balance operativo para logística y e-commerce: tarjetas de tarifas, cotizador interactivo por zonas, selectores de servicio y números tabulares. |
| **Variance** | `7` | Asimetría intencional: layouts en split-screen 60/40, bento grids con tarjetas destacadas y matrices de cobertura urbana en Mar del Plata. |
| **Motion Intent** | `6` | Fluido y funcional: micro-compresión física en botones pastilla (`scale 0.97`), marquesina pausable al hover y aceleración por GPU con `--ease-out-ui`. |

---

## 1. Visual Theme & Atmosphere

El universo visual de **Envíos DosRuedas** proyecta la energía, precisión y agilidad del reparto urbano en moto y la logística e-commerce en Mar del Plata.  
La atmósfera combina la **señalética vial de alta visibilidad** con la **limpieza arquitectónica de una plataforma tecnológica moderna**.  

No hay lugar para el aburrimiento corporativo ni para la estética oscura genérica: el lienzo es blanco inmaculado, los encabezados golpean con mayúsculas contundentes en azul profundo (#0950F6), y el amarillo vial (#FFEC01) actúa como detonador de acción inmediata. Transmite rapidez sin caos, cercanía local con rigor logístico, y una presencia visual reconocible al instante en cualquier pantalla.

---

## 2. Color Palette & Roles (La Ley de Tres Colores)

El sistema cromático está estrictamente calibrado en **tres colores canónicos**. Queda absolutamente prohibido el uso de negros neutros (`#000000`), grises genéricos de Tailwind (`#6B7280`, `#9CA3AF`, etc.) o degradados violeta/neón.

```
┌─────────────────────────────────┬─────────────────────────────────┬─────────────────────────────────┐
│          AZUL VIBRANTE          │          AMARILLO VIAL          │           BLANCO PURO           │
│             #0950F6             │             #FFEC01             │             #FFFFFF             │
│    Tope Máximo de Oscuridad     │      Acento & Señal Vial        │          Lienzo Único           │
│   (Primario, Títulos, Ink)      │      (CTAs, ≤15% Superficie)    │      (Fondos, Superficies)      │
└─────────────────────────────────┴─────────────────────────────────┴─────────────────────────────────┘
```

### 2.1. Escala Tonal Calibrada

#### Azul Vibrante (Tope de Oscuridad: `#0950F6`)
* **Azul Bezel / Suave (`--color-brand-blue-50`: `#E6EEFE`)** — Fondo de bisel exterior (`double-bezel-outer`), fondos de tarjetas secundarias, placeholders y skeleton loaders.
* **Azul Estructural (`--color-brand-blue-100`: `#BACEFD`)** — Borde de contención, líneas divisorias sutiles, líneas de progreso inactivas.
* **Azul Interacción (`--color-brand-blue-200`: `#8EAFFB`)** — Hover en bordes de tarjetas, trazos SVG secundarios.
* **Azul Borde Reposo (`--color-brand-blue-300`: `#628FF9`)** — Bordes de campos de formulario en reposo, anillos de foco secundarios.
* **Azul Icono (`--color-brand-blue-400`: `#3570F8`)** — Iconografía decorativa sobre blanco, texto muted grande (≥24px).
* **Azul Canónico Primario (`--color-brand-blue-500`: `#0950F6`)** — Encabezados H1/H2, botones principales, fondo de header y drawer móvil, tinta base del texto.

#### Amarillo Vial (Acento & Acción — Cobertura ≤ 15%)
* **Amarillo Tinte (`--color-brand-yellow-50`: `#FFFDE6`)** — Fondo de servicio o tarifa seleccionada.
* **Amarillo Badge (`--color-brand-yellow-100`: `#FFFAB8`)** — Insignias de confirmación y halos sutiles.
* **Amarillo Borde Foco (`--color-brand-yellow-200`: `#FFF78A`)** — Borde de elemento activo.
* **Amarillo Resaltado (`--color-brand-yellow-300`: `#FFF45C`)** — Detalles mono y precios sobre fondos azules.
* **Amarillo Hover (`--color-brand-yellow-400`: `#FFF12E`)** — Estado hover de botones CTA y acceso a WhatsApp.
* **Amarillo Canónico CTA (`--color-brand-yellow-500`: `#FFEC01`)** — Botones de llamada a la acción, badges de urgencia, píldoras knockout, franja de acento en footer.
* **Amarillo Presionado (`--color-brand-yellow-600`: `#E6D400`)** — Estado active de botones CTA.

#### Blanco Puro (`--color-white`: `#FFFFFF`)
* Lienzo base de la página, tarjetas interiores, texto de máximo contraste sobre fondos azules.

### 2.2. Reglas Inviolables de Contraste
1. **Texto sobre Amarillo (`#FFEC01`):** **SIEMPRE Azul Canónico (`#0950F6`)**. El texto blanco sobre amarillo está BANEADO (falla de accesibilidad).
2. **Texto sobre Azul (`#0950F6`):** **SIEMPRE Blanco (`#FFFFFF`)** o Amarillo (`#FFEC01`).
3. **Capas y Overlays:** Prohibido oscurecer con negro. Los menús desplegables y hovers sobre azul se resuelven con iluminación de marca (`bg-white/10`, `bg-white/15` o `border-white/15`).

---

## 3. Typography Rules

La arquitectura tipográfica equilibra el impacto condensado de la señalética vial con la legibilidad cómoda de textos largos en móviles.

| Rol | Familia Tipográfica | Peso | Tracking | Leading | Caso / Transformación |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **Display** | `Anton` (fallback: `sans-serif`) | 900 | `-0.025em` a `-0.05em` | `0.85` – `0.9` | **UPPERCASE obligatorio**. Títulos de sección H1/H2, cifras gigantes en estadísticas. |
| **Subheading** | `Bebas Neue` (fallback: `sans-serif`) | 700 | `+0.05em` | `1.0` – `1.1` | **UPPERCASE obligatorio**. Botones pastilla, chips de navegación, badges, nombres de servicio. |
| **Body / Sans** | `Outfit` (fallback: `IBM Plex Sans`) | 300, 400, 500, 600 | `0em` | `1.6` | **Sentence case normal**. Textos de lectura, párrafos descriptivos, etiquetas de formularios. Max 65ch. |
| **Mono** | `Geist Mono` (fallback: `monospace`) | 400, 600 | `0em` | `1.2` | `tabular-nums`. Cotizaciones, distancias (ej. "0 a 3 km"), plazos (ej. "3 HS"), código de seguimiento. |

### Reglas Tipográficas
* **Escala Fluida:** Encabezados Display escalan mediante `clamp(2.25rem, 5vw, 4.5rem)` para evitar desbordes en móviles.
* **Equilibrio de Textos:** Usar `text-wrap: balance` en títulos para evitar palabras huérfanas.
* **Fuentes Prohibidas:** BANEADO `Inter` (genérico). BANEADAS todas las fuentes serif clásicas (`Times New Roman`, `Georgia`, `Garamond`).

---

## 4. Component Stylings & Signatures

### 4.1. Double-Bezel (Firma de Contenedor Oficial)
Es el contenedor de firma que enmarca tarjetas principales, cotizadores y secciones clave:
* **Outer Bezel (`.double-bezel-outer`):**
  * Fondo: `rgba(230, 238, 254, 0.8)` (`brand-blue-50/80`).
  * Borde: `1px solid #BACEFD` (`brand-blue-100`).
  * Radio: `1.25rem` a `1.5rem` (`rounded-xl` / `rounded-2xl`).
  * Padding: `0.5rem` (`8px`).
  * Sombra: `--shadow-float` (`0 25px 50px -12px rgba(9, 80, 246, 0.15)`).
  * Hover: Transición a borde `#628FF9` y elevación `--shadow-antigravity-deep`.
* **Inner Bezel (`.double-bezel-inner`):**
  * Fondo: `#FFFFFF`.
  * Radio: `1rem` a `1.125rem` (`rounded-lg` / `rounded-xl`).
  * Padding: `1.5rem` a `2rem` (`24px` a `32px`) — nunca texto pegado al borde.
  * Borde: `1px solid rgba(230, 238, 254, 0.5)`.
  * Sombra: Inset sutil `inset 0 2px 4px rgba(9, 80, 246, 0.06)`.
* **Variante Dark (`.double-bezel-inner-dark`):**
  * Fondo: `#0950F6`. Color de texto forzado: `#FFFFFF`. Borde: `1px solid rgba(255, 255, 255, 0.15)`.

### 4.2. Botón CTA Nested Pill (`.cta-nested-pill`)
El elemento de acción primaria de la interfaz:
* **Forma:** Píldora redondeada completa (`rounded-full`), altura mínima `46px` (touch target accesible).
* **Tipografía:** `Bebas Neue`, uppercase, tracking `+0.05em`, peso 700.
* **Paleta:** Fondo `#FFEC01`, texto `#0950F6`, sombra direccional `--shadow-cta-glow`.
* **Micro-Interacción:**
  * **Hover:** Elevación física `translateY(-2px)`, cambio a `#FFF12E`.
  * **Ícono anidado (`.cta-nested-icon`):** Círculo en `rgba(9, 80, 246, 0.1)` que se desplaza `translateX(4px)` al hover.
  * **Active (Click táctil):** Micro-compresión háptica `transform: scale(0.97)` en 140ms.

### 4.3. Knockout Badges (`.knockout-badge` / `.knockout-pill`)
* Pastilla o bloque en amarillo canónico `#FFEC01` con texto en azul `#0950F6` en `Bebas Neue`.
* Se utiliza para destacar el servicio estrella (*"MERCADO ENVÍOS FLEX"*, *"FRANJA 3 HS"*, *"TARIFA PLANA"*).
* Sombra teñida direccional: `0 8px 24px rgba(9, 80, 246, 0.18), 0 2px 6px rgba(255, 236, 1, 0.2)`.

### 4.4. Header Canónico & Drawer Móvil
* **Desktop:** Barra fija superior en `#0950F6` con borde `border-white/10`, isotipo oficial `LogoEnviosDosRuedas.webp` con elevación en hover (`group-hover:rotate-6`).
* **Dropdowns:** Paneles en `#0950F6` con borde `border-white/15` y sombra elevada. Links con hover vítreo `hover:bg-white/10` y texto en `#FFEC01`.
* **Drawer Móvil:** Diálogo lateral `max-w-80` con altura dinámica `h-[100dvh]` (para prevenir saltos de barra en iOS/Android), backdrop en `bg-brand-blue-500/70` con desenfoque `backdrop-blur-md`.

### 4.5. Formularios & Cotizador
* Labels superiores en `Outfit` peso 500/600 o `Bebas Neue`.
* Inputs con borde en reposo `#628FF9`, foco con anillo de acento `#FFEC01` (`ring-2 ring-brand-yellow-500`).
* Mensajes de error en línea bajo el campo, nunca en alert flotante genérico.

---

## 5. Hero Section Architecture

El hero es la declaración de intenciones y debe estructurarse con asimetría y jerarquía:
* **Estructura Split Asimétrica (60/40):** Columna izquierda dominante con H1 en `Anton` Display, párrafo de valor en `Outfit`, y CTA primario `cta-nested-pill`. Columna derecha con tarjeta biselada (`double-bezel`) interactiva o visual de logística.
* **Restricción de CTAs:** Máximo un botón CTA primario destacado por hero. No duplicar con botones secundarios débiles tipo "Ver más".
* **Prohibición de Texto de Relleno:** Prohibido usar "Scroll para explorar", flechitas rebotando o chevrons decorativos.
* **Cero Superposición Ilegible:** El texto nunca debe montarse sobre imágenes o ilustraciones de fondo sin una separación clara de capa.

---

## 6. Layout & Grid Principles

* **Grid-First:** Grids CSS nativos (`grid grid-cols-1 md:grid-cols-2 lg:grid-cols-12`) con gutters consistentes (`gap-6` a `gap-8`).
* **Baneada la Fila de 3 Tarjetas Idénticas:** En su lugar, utilizar layouts Bento con una tarjeta dominante (ej. Envíos Flex o Express al 60% del ancho) y tarjetas complementarias al 40%.
* **Contención de Ancho:** Ancho máximo unificado `max-w-7xl` (`80rem` / `1280px`) centrado con padding horizontal (`px-4 sm:px-6 lg:px-8`).
* **Espaciado Vertical:** Ritmo vertical generoso mediante `py-16 sm:py-24` (`clamp(4rem, 8vw, 6rem)`). Más espacio por encima de un encabezado que por debajo.
* **Viewport Móvil Dinámico:** Secciones de pantalla completa usan `min-h-[100dvh]`, jamás `h-screen`.

---

## 7. Motion & Interaction Philosophy

El movimiento en Envíos DosRuedas es enérgico, preciso y sobrio. No hay acrobacias gratuitas.

### 7.1. Tokens de Movimiento Oficiales
```css
:root {
  --ease-out-ui: cubic-bezier(0.23, 1, 0.32, 1);   /* Llegadas, expansiones de menú y hovers */
  --ease-snappy: cubic-bezier(0.16, 1, 0.3, 1);   /* Entradas dinámicas de alta aceleración */
  --t-press: 140ms;                               /* Feedback físico en click */
  --t-hover: 180ms;                               /* Transición de color y elevación */
  --t-dropdown: 200ms;                            /* Apertura de menús */
  --t-modal: 250ms;                               /* Entrada de drawer/diálogo */
}
```

### 7.2. Principios de Movimiento
* **Aceleración por GPU Exclusiva:** Animar únicamente `transform` y `opacity`. Prohibido usar `transition-all` indiscriminadamente.
* **Pausa al Cursor:** Toda animación continua (como el carrusel de redes o logos) se pausa automáticamente al hover (`:hover { animation-play-state: paused; }`).
* **Indicadores Calmos:** Cero animaciones en bucle perpetuo (`animate-ping`) en elementos estáticos. Las luces de estado se mantienen sólidas y limpias.
* **Reducción de Movimiento Obligatoria:**
  ```css
  @media (prefers-reduced-motion: reduce) {
    html { scroll-behavior: auto !important; }
    *, *::before, *::after {
      animation-duration: 0.01ms !important;
      animation-iteration-count: 1 !important;
      transition-duration: 0.01ms !important;
    }
  }
  ```

---

## 8. Anti-Patterns (Banned AI Clichés)

Lista estricta de patrones prohibidos en cualquier nueva pantalla o componente:

1. ❌ **No emojis en la UI:** Usar exclusivamente iconografía vectorial consistente (Lucide Icons con trazo `2px` o `2.5px`).
2. ❌ **No negro puro (`#000000`):** El tope de oscuridad de la marca es el Azul `#0950F6`.
3. ❌ **No texto blanco sobre fondo amarillo:** Falla crítica de contraste; el texto sobre amarillo siempre es azul `#0950F6`.
4. ❌ **No grises neutros genéricos:** Prohibido el uso de `gray-500`, `slate-600` o `zinc-400`. Las atenuaciones se hacen con transparencias de azul o blanco.
5. ❌ **No fuente `Inter`:** Usar el stack oficial: `Anton` (Display), `Bebas Neue` (Subheading), `Outfit` (Sans), `Geist Mono` (Mono).
6. ❌ **No fuentes serif clásicas en software o interfaces:** Prohibido `Times New Roman`, `Georgia` o `Garamond`.
7. ❌ **No halos de neón plano (*zero-offset*):** BANEADO `box-shadow: 0 0 25px #FFEC01`. Usar sombras direccionales físicas teñidas con offset vertical.
8. ❌ **No filas genéricas de 3 tarjetas idénticas:** Utilizar arquitectura Bento o grids asimétricos con jerarquía evidente.
9. ❌ **No tarjetas anidadas sin función:** No meter cajas con borde y sombra dentro de otra caja con borde y sombra; usar divisores lineales o espaciado negativo.
10. ❌ **No `h-screen` en contenedores móviles:** Utilizar `100dvh` para evitar el brinco del viewport en Safari y Chrome móvil.
11. ❌ **No textos de relleno cliché:** Prohibido "Scroll to explore", "Swipe down", o adjetivos vacíos de IA ("Seamless", "Elevate", "Next-gen").
12. ❌ **No datos o estadísticas falsas:** Si una cifra no es real del negocio, etiquetarla honestamente como placeholder y no inventar métricas tipo "99.9% Uptime SLA".
