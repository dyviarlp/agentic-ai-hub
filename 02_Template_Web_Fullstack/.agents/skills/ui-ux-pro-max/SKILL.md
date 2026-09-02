---
name: ui-ux-pro-max
description: Arquitectura de interfaces web de alto impacto visual, jerarquía tipográfica Google Fonts, paletas HSL y diseño responsivo sin clichés de IA.
---

# UI/UX Pro Max: Arquitectura de Interfaces Web de Alto Impacto

> **Nivel de Activación:** Nivel 1 (Fase de Diseño y Maquetación Frontend).  
> **Objetivo:** Garantizar interfaces con acabado visual premium, jerarquía visual rigurosa, legibilidad excepcional y cero apariencia genérica de IA.

---

## 1. Reglas Maestras de Identidad Visual

1. **Tipografía Curada y Jerárquica:**
   - Selección tipográfica: `Inter`, `Outfit` o `Roboto` desde Google Fonts.
   - Escala modular coherente: `display` (48-64px), `h1` (36-40px), `h2` (28-32px), `h3` (22-24px), cuerpo (16px, line-height 1.6-1.75).
   - Contraste visual entre títulos semibold/bold y texto base regular/medium.

2. **Paletas Cromáticas HSL / Tokens Semánticos:**
   - Prohibidos colores puros primarios (`#ff0000`, `#0000ff`).
   - Construcción de gamas armónicas basadas en HSL:
     - Fondo (`--bg`): slate/zinc oscuro (`hsl(222, 47%, 7%)`) o blanco perla cálido (`hsl(0, 0%, 98%)`).
     - Superficie (`--surface`): elevación visual con bordes sutiles de 1px.
     - Acento (`--accent`): tonos calibrados para contraste WCAG AA (`ratio > 4.5:1`).

3. **Profundidad y Glassmorphism Sutil:**
   - Fondos con gradientes sutiles y mallas de luz (`radial-gradient`).
   - Tarjetas flotantes con `backdrop-filter: blur(12px)` y borde `1px solid rgba(255, 255, 255, 0.08)`.
   - Sombras multicapa suaves (`box-shadow: 0 4px 20px -2px rgba(0, 0, 0, 0.3)`).

---

## 2. Experiencia de Usuario y Conversión

- **Espaciado Generoso:** Aplicar principios de espaciado modular (`gap-4`, `gap-6`, `gap-8`, `gap-12`) para evitar saturación visual.
- **Llamadas a la Acción (CTA) Inequívocas:** Botones principales prominentes, con estados de carga animados (`isSubmitting`) y retroalimentación táctil/hover inmediata.
- **Cero Placeholders:** Utilizar contenido verosímil y assets visuales optimizados (WebP/AVIF o SVG nítidos).
