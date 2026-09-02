# Memoria de Dominio 01: Core Web Vitals y Rendimiento Web (2026)

> **Última validación:** 2026-09-02  
> **Ámbito:** Optimización de tiempos de carga, interactividad y estabilidad visual para Next.js, React y Astro.

---

## 🎯 Invariantes y Métricas Objetivo (CWV 2026)

| Métrica | Umbral Crítico | Indicador Clave | Palanca Principal |
| :--- | :--- | :--- | :--- |
| **LCP (Largest Contentful Paint)** | `< 2.0s` | Renderizado del bloque visible primario | Preload de fuentes, `priority` en imágenes hero, streaming SSR. |
| **INP (Interaction to Next Paint)** | `< 200ms` | Latencia de respuesta en interacción | Desglose de tareas largas, `startTransition`, delegación de eventos. |
| **CLS (Cumulative Layout Shift)** | `< 0.1` | Desplazamientos inesperados en layout | Dimensiones explícitas (`width`/`height` o `aspect-ratio`), font-display swap. |

---

## 🛠️ Reglas Preventivas y Patrones de Arquitectura

### 1. Eliminación Radical de Waterfalls

- **Prohibido el `await` secuencial:** Agrupar llamadas independientes mediante `Promise.all([fetchA(), fetchB()])`.
- **Streaming con Suspense:** Envolver secciones con datos lentos en `<Suspense fallback={<Skeleton />}>` para entregar el HTML inicial en <500ms.
- **RSC por defecto:** Mantener componentes como React Server Components (RSC) salvo necesidad estricta de estado local o event listeners (`'use client'`).

### 2. Optimización de Assets y Fuentes

- **Imágenes:** Usar siempre `<Image />` de Next.js o `<Image />` de Astro. Marcar únicamente la imagen del Hero con `priority` (y fetchpriority="high"). Formatos automáticos AVIF/WebP.
- **Fuentes Web:** Cargar vía `next/font/google` con `display: 'swap'` y `subsets: ['latin']`. Evitar llamadas manuales a `@import` en hojas de estilo globales.

### 3. Zero-JS Bloat y CSS-First

- Priorizar CSS moderno antes de instalar paquetes npm para interactividad:
  - Modales: Usar el elemento nativo `<dialog>` o la API nativa de `popover`.
  - Animaciones de scroll: Usar `@keyframes` con `animation-timeline: view()` / `scroll()`.
  - Acordeones: Usar `<details>` y `<summary>` nativos estilizados.
- **Dynamic Imports:** Cargar componentes pesados (gráficos, editores, mapas, GSAP) con `dynamic(() => import('./HeavyComponent'), { ssr: false })`.
