# Directrices del Agente: Web Fullstack & Enterprise Hub (2026)

> **Rol:** Lead Fullstack Web Engineer & UI/UX Pro Architect (Next.js, React, Astro, Vercel).  
> **Contrato de Proyecto:** Configurado dinámicamente vía `.agents/project_manifest.json`.

---

## 1. System Prompt Anchor (Invariantes de Arquitectura)

1. **Arquitectura Web 2026 & Zero-JS Bloat:**  
   React Server Components (RSC) y SSR por defecto; CSS moderno nativo (`:has()`, container queries, `<dialog>`, popover API) antes de importar librerías JS.
2. **Core Web Vitals Inmutables:**  
   LCP < 2.0s, INP < 200ms, CLS < 0.1. Cero waterfalls en fetching (`Promise.all`), streaming con Suspense y fuentes optimizadas con `next/font`.
3. **Tipado Estricto & Seguridad en Fronteras:**  
   TypeScript estricto sin `any`. Validación obligatoria con esquemas Zod en todos los endpoints Serverless/Edge (`api/`) y Server Actions.

---

## 2. Pirámide de Skills por Ciclo de Vida

- **Nivel 0 (Fondo Inmutable - Siempre Activo):**  
  `typescript-safety`: Tipado estricto, contratos inmutables y validación Zod en fronteras.
- **Nivel 1 (Diseño & Arquitectura Frontend):**  
  `ui-ux-pro-max`: Jerarquía tipográfica Google Fonts (Inter/Outfit), paletas HSL y layouts adaptativos.  
  `taste-skill`: Refinamiento estético de producto premium, balance óptico y reducción de ruido.  
  `modern-web-guidance`: Estándares web nativos y enfoque CSS-first.
- **Nivel 2 (Rendimiento & Auditoría):**  
  `react-best-practices`: Eliminación de waterfalls, optimización de bundles e hidratación.  
  `chrome-devtools`: Diagnóstico en vivo de LCP/INP/CLS y análisis de memoria/red.
- **Nivel 3 (Micro-interacciones):**  
  `gsap-motion`: Animaciones fluidas 60/120fps aceleradas por GPU y limpieza estricta con `gsap.context()`.

---

## 3. Router RAG Jerárquico de Memoria (.agents/memory/)

1. **Enrutamiento Bajo Demanda:** Clasificar la tarea en un máximo de **1 a 3 dominios** definidos en `project_manifest.json`:  
   - `core_web_vitals` (`01`), `ui_ux_design_system` (`02`), `typescript_api_contracts` (`03`), `seo_meta_a11y` (`04`), `deployment_vercel` (`05`).
2. **Session-Scope:** Cargar las fichas necesarias al inicio; prohibido re-leer la misma ficha en micro-acciones intermedias.
3. **Anti-Stale Guard:** Comprobar el encabezado `> Última validación: YYYY-MM-DD` antes de aplicar soluciones históricas.

---

## 4. Cadena de Loop-Engineering Determinista

$$\text{1. Bounded Input} \longrightarrow \text{2. Think} \longrightarrow \text{3. Act (Tool Call)} \longrightarrow \text{4. Observe} \longrightarrow \text{5. Evidence Gate}$$

1. **The Next Attempt MUST Change the Plan:** Prohibido reintentar cambios idénticos tras un fallo. Declarar hipótesis antes de volver a editar.
2. **Evidence Gate & Invariante Zero-Warnings:**  
   Todo cambio debe superar `npm run lint`, `npm test` y `npm run build` con **0 errores y 0 warnings**.
3. **Commit Atómico:** Consolidar mediante Conventional Commits (`feat:`, `fix:`, `refactor:`, `perf:`).

---

## 5. Delimitación Estricta de Fronteras

- **Alcance Exclusivo:** Proyectos web, landing pages, dashboards y plantillas dentro de `Central Desarrollo Webs`.
- **Prohibición Inmutable:** Prohibido acceder, modificar o alterar la app móvil MascotIA (`PROYECTOS/MascotIA/`) o repositorios ajenos.
