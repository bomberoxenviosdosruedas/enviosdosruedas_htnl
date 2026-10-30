# Envíos DosRuedas — Manual de Identidad Visual & Brand Guidelines

> **Versión:** 1.0.0 — Canónica  
> **Ámbito:** Sitios web, aplicaciones, componentes y piezas gráficas digitales de *Envíos DosRuedas*.  
> **Basado en:** tokens unificados (`tokens.json`, `tokens.css`) y auditoría de interfaz.

---

## 1. Filosofía de Marca y ADN Visual

**Envíos DosRuedas** es el referente de logística ágil, mensajería en moto y soluciones e-commerce en Mar del Plata.  
El lenguaje gráfico transmite:
* **Velocidad y Precisión:** Tipografías dinámicas y condensadas de alto impacto.
* **Seguridad y Confianza:** Azul vibrante estructurado con bordes definidos.
* **Señalética Vial y Urgencia Positiva:** Amarillo vial de alta visibilidad para acciones clave.

---

## 2. La Ley de Tres Colores (The 3-Color Rule)

La interfaz se rige estrictamente por **tres colores fundamentales**. Queda expresamente prohibido introducir negros puros (`#000000`), grises neutros genéricos (`#6B7280`, `#9CA3AF`, etc.) o matices no aprobados.

```
┌────────────────────────┐  ┌────────────────────────┐  ┌────────────────────────┐
│      AZUL VIBRANTE     │  │     AMARILLO VIAL      │  │      BLANCO PURO       │
│        #0950F6         │  │        #FFEC01         │  │        #FFFFFF         │
│   Tope de Oscuridad    │  │     Acento & CTAs      │  │      Lienzo Base       │
│    (Superficie/Ink)    │  │    (≤ 15% Cobertura)   │  │       (Espacio)        │
└────────────────────────┘  └────────────────────────┘  └────────────────────────┘
```

### 2.1. Escala Cromática Oficial

#### Azul Vibrante (Tope máximo de oscuridad: `#0950F6`)
| Paso | Hex | Rol & Aplicación |
| :--- | :--- | :--- |
| **50** | `#E6EEFE` | Fondos secundarios suaves, bezel exterior, skeleton loader, hover sutil |
| **100** | `#BACEFD` | Bordes estructurales, divisores de sección, líneas de progreso inactivas |
| **200** | `#8EAFFB` | Borde en hover de tarjetas, trazos SVG secundarios |
| **300** | `#628FF9` | Bordes de inputs en reposo, anillos de foco secundarios |
| **400** | `#3570F8` | Iconografía, textos muted grandes (≥24px), hover de fondos azules |
| **500** | `#0950F6` | **Color canónico primario**: Títulos H1/H2, botones principales, foco, tinta base |

#### Amarillo Vial (Señal y Acción — Cobertura ≤ 15%)
| Paso | Hex | Rol & Aplicación |
| :--- | :--- | :--- |
| **50** | `#FFFDE6` | Fondo de tarjeta de servicio seleccionada |
| **100** | `#FFFAB8` | Badges, chips de estado completado |
| **200** | `#FFF78A` | Borde de elemento seleccionado o enfocado |
| **300** | `#FFF45C` | Detalles de código mono sobre fondos azules |
| **400** | `#FFF12E` | Hover de botones CTA principales y WhatsApp |
| **500** | `#FFEC01` | **Acento canónico**: Botones de llamada a la acción (CTA), badges urgentes, precio |
| **600** | `#E6D400` | Estado presionado (`active`) de los botones CTA |

#### Blanco (`#FFFFFF`)
* Lienzo principal de lectura, contraste de alto impacto sobre azul, fondos de tarjetas interiores.

---

## 3. Reglas Inviolables de Contraste y Accesibilidad

1. **Sobre fondo Amarillo (`#FFEC01`):**  
   * El texto e iconografía deben ser **SIEMPRE Azul Canónico (`#0950F6`)**.  
   * ❌ **NUNCA usar texto blanco sobre fondo amarillo** (contraste ilegible y fallo de accesibilidad WCAG AAA).
2. **Sobre fondo Azul (`#0950F6`):**  
   * Texto de lectura y títulos en **Blanco (`#FFFFFF`)**.  
   * Acentos, micro-destacados o precios en **Amarillo (`#FFEC01`)**.
3. **Overlays, Menús y Estados Hover:**  
   * Prohibido oscurecer con `black/15` o `black/20`.  
   * Las capas de interacción sobre azul se resuelven con:  
     * Iluminación: `bg-white/10` o `bg-white/15`.  
     * Matiz de marca: `bg-brand-blue-50/15` o `border-white/15`.

---

## 4. Sistema Tipográfico Oficial

| Rol | Familia | Peso / Estilo | Tracking | Uso |
| :--- | :--- | :--- | :--- | :--- |
| **Display** | `Anton` | 900 / Normal | `-0.025em` a `-0.05em` | Títulos principales (H1, H2), números gigantes de estadísticas. En mayúsculas (`uppercase`). |
| **Subheading** | `Bebas Neue` | 700 / Normal | `+0.05em` | Subtítulos de sección, navegación, botones pill, chips de categoría. En mayúsculas. |
| **Sans / Body** | `Outfit` | 300, 400, 500, 600 | Normal (`0em`) | Todo el texto de lectura, párrafos descriptivos, etiquetas de formulario, legal. |
| **Mono** | `Geist Mono` | 400, 600 | Normal | Números de guía, precios, tarifas, tiempos de entrega (`tabular-nums`). |

---

## 5. Geometría de Firma y Componentes Clave

### 5.1. Double-Bezel (Firma Geométrica de Contenedor)
* **Exterior (`double-bezel-outer`):** Fondo `rgba(230, 238, 254, 0.8)`, borde `1px solid #BACEFD`, radio `16px` (`rounded-xl` o `2xl`), sombra flotante teñida.
* **Interior (`double-bezel-inner`):** Fondo blanco `#FFFFFF`, radio `12px` (`rounded-lg`), borde `1px solid rgba(230, 238, 254, 0.5)`.

### 5.2. Botón CTA Nested Pill
* **Forma:** Píldora redondeada completa (`rounded-full`, min-height 44px).
* **Tipografía:** `Bebas Neue` en mayúsculas, tracking amplio (`0.05em`), font-weight 700.
* **Comportamiento dinámico:**
  * Reposo: Fondo `#FFEC01`, texto `#0950F6`, sombra `--shadow-cta-glow`.
  * Hover: Fondo `#FFF12E`, elevación física `translateY(-1px)`.
  * Active: Escala `scale(0.97)`.
  * Ícono de flecha/acción: Contenedor circular con micro-desplazamiento `translateX(4px)` al pasar el cursor.

### 5.3. Sombras Teñidas (Tinted Shadows)
Nunca se usan sombras negras o grises transparentes. Toda elevación proyecta color de marca:
* **Elevación estándar:** `0 16px 40px rgba(9, 80, 246, 0.18)`
* **Flotación profunda:** `0 25px 50px -12px rgba(9, 80, 246, 0.15)`
* **Resplandor CTA:** `0 0 28px rgba(255, 236, 1, 0.45), 0 8px 24px rgba(9, 80, 246, 0.18)`

---

## 6. Checklist de Validación (Do's & Don'ts)

| ✅ Qué Hacer (Do's) | ❌ Qué Evitar (Don'ts) |
| :--- | :--- |
| Usar `#0950F6` como fondo oscuro y tope de sombra. | Usar `#000000`, `gray-800` o sombras grises descoloridas. |
| Texto azul `#0950F6` sobre botones amarillos. | Texto blanco `#FFFFFF` sobre botones amarillos. |
| Aplicar `double-bezel` en tarjetas destacadas y cotizadores. | Usar tarjetas planas sin jerarquía de borde. |
| Usar `Anton` y `Bebas Neue` exclusivamente en mayúsculas (`uppercase`). | Usar tipografías display en minúsculas o textos largos de párrafo. |
| Utilizar `Outfit` para garantizar lectura cómoda en móviles. | Sustituir tipografías del sistema por fuentes genéricas como Arial o Times. |

---

## 7. Gobernanza del Logotipo (Circular Patrimonial vs. Adaptable)

Con el fin de preservar el reconocimiento histórico de más de 7 años de la empresa en Mar del Plata, se establece la siguiente directiva:

### 7.1. Logotipo Circular Patrimonial (Sello de Garantía)
* **Intocabilidad Cromática:** Se mantienen intactos los colores preexistentes del logotipo circular original tal como lo requiere la dirección. No se fuerzan a la paleta del sitio.
* **Optimización Vectorial:** Se optimizan trazos y curvas en formato SVG/WebP para evitar pixelado o artefactos en pantallas Retina.
* **Cápsula de Montaje:** Sobre fondos oscuros o de color de la web (`#0950F6`), se aplica un halo de aislamiento perimetral blanco (`2px a 4px`) o una pastilla de montaje neutra para garantizar autonomía visual.

### 7.2. Logotipos Horizontales y Favicon (Adaptados a la Marca)
* **Versión Horizontal (Navbar y Cabeceras):** Integra el isotipo vectorial depurado con la marca denominativa `"Envíos DosRuedas"` adoptando 100% los colores de marca (`#0950F6` sobre blanco, o `#FFFFFF` y `#FFEC01` sobre azul).
* **Favicon e Iconos de Sistema:** Adaptados a los contrastes del sistema de diseño (Azul `#0950F6` de base con acentos Amarillo `#FFEC01` y blanco) para una visibilidad perfecta en navegadores móviles y de escritorio.

