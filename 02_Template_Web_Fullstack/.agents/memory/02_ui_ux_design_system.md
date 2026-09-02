# Memoria de Dominio 02: Sistema de Diseño UI/UX Pro y Estética Web (2026)

> **Última validación:** 2026-09-02  
> **Ámbito:** Identidad visual, tipografía, paletas cromáticas HSL, micro-interacciones y layouts responsivos.

---

## 🎨 Principios Visuales No Negociables (Cero IA-Cliché)

1. **Tipografía Curada:**
   - Tipografía principal: **Inter** o **Outfit** vía Google Fonts.
   - Jerarquía tipográfica estricta con escala modular: display (`text-5xl`/`text-6xl`), títulos semánticos `h1`-`h4`, y cuerpo de texto accesible (`text-base` con `line-height: 1.6`).
   - Prohibido el uso de fuentes por defecto del sistema sin estilizar.

2. **Paletas Armónicas HSL / OKLCH:**
   - Prohibidos colores genéricos planos (`#ff0000`, `#00ff00`).
   - Definición de tokens semánticos en HSL o variables CSS:
     - `background`: Fondos oscuros profundos (`hsl(224, 71%, 4%)` o variantes slate/zinc).
     - `surface`: Capas con elevación sutil (`hsl(220, 13%, 10%)`).
     - `primary`: Acentos vibrantes equilibrados con contraste AA (`hsl(250, 84%, 54%)`).
     - `border`: Separadores translúcidos (`hsla(220, 13%, 90%, 0.08)`).

3. **Glassmorphism y Profundidad Sutil:**
   - Fondos con gradientes radiales difuminados (`radial-gradient(circle at top, ...)`) combinados con tarjetas en `backdrop-filter: blur(12px)`.
   - Bordes ultrafinos con gradiente (`border: 1px solid rgba(255, 255, 255, 0.1)`).

---

## 📐 Layouts Fluidos y CSS Moderno (2026)

1. **Selector `:has()`:**
   - Aplicar estados contextuales sin necesidad de JavaScript (ej. `:has(input:focus)`, `:has([aria-expanded="true"])`).
2. **Container Queries (`@container`):**
   - Construir componentes verdaderamente modulares cuyo diseño responda al ancho de su contenedor padre (`container-type: inline-size`), no solo al viewport global (`@media`).
3. **CSS Subgrid:**
   - Alinear elementos hijos dentro de tarjetas anidadas sin romper la cuadrícula maestra (`grid-template-rows: subgrid`).
4. **Micro-interacciones y Feedback:**
   - Transiciones suaves (`cubic-bezier(0.16, 1, 0.3, 1)` o resortes).
   - Efectos `hover`, `active` y `:focus-visible` explícitos con anillo accesible de contraste alto.
