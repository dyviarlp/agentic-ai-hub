# Memoria de Dominio 04: SEO Técnico y Accesibilidad WCAG AA (2026)

> **Última validación:** 2026-09-02  
> **Ámbito:** Accesibilidad web, etiquetas meta, indexación en motores de búsqueda y datos estructurados.

---

## ♿ Invariantes de Accesibilidad (WCAG 2.2 AA)

1. **HTML5 Semántico Estricto:**
   - Un único `<h1>` por página representativo del contenido principal.
   - Jerarquía lógica estricta: `<h1>` ➔ `<h2>` ➔ `<h3>` sin saltos arbitrarios.
   - Uso de tags semánticos: `<header>`, `<nav>`, `<main>`, `<article>`, `<aside>`, `<footer>`. Prohibido crear estructuras basadas enteramente en `<div>`.
2. **Navegación por Teclado:**
   - Todos los elementos interactivos (`button`, `a`, `input`, `select`) deben ser alcanzables por tabulación secuencial.
   - Anillos de enfoque visibles obligatorios con `outline: 2px solid var(--focus-ring)` o clases Tailwind `focus-visible:ring-2`.
   - Modales deben implementar **Focus Trap** devolviendo el foco al disparador al cerrarse (`ESC`).
3. **Contraste Cromático:**
   - Razón de contraste mínima de 4.5:1 para texto normal y 3:1 para texto grande o elementos gráficos esenciales.

---

## 🔍 SEO Técnico y Metadatos Dinámicos

1. **Metadatos OpenGraph y Twitter Cards:**
   - Implementar `generateMetadata` en Next.js (o frontmatter en Astro) con:
     - `title` conciso (<60 caracteres).
     - `description` de alto impacto (<160 caracteres).
     - `openGraph: { images: ['/og-image.png'], type: 'website', locale: 'es_ES' }`.
     - `alternates: { canonical: 'https://...' }`.
2. **Datos Estructurados (JSON-LD):**
   - Inyectar schemas Schema.org (`Organization`, `WebSite`, `Product`, `FAQPage`) validados en un script `<script type="application/ld+json">`.
3. **Rutas Clave de Rastreo:**
   - Todo proyecto debe generar dinámicamente `sitemap.xml` y `robots.txt`.
