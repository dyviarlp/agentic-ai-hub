# Memoria de Dominio 06: Catálogo de Servicios Web & Arquitectura de Contenidos (Blueprint)

> Última validación: 2026-09-03 | Estado: Plantilla Oficial Enterprise Hub  
> Single Source of Truth (SSOT) para propuestas de valor, catálogo de servicios y arquitectura de copys web.  
> Evita el escaneo por fuerza bruta de componentes `.tsx` o páginas renderizadas.

---

## 📋 Catálogo Estructurado de Servicios de Desarrollo Web

| Servicio / Solución | Stack Tecnológico | Invariantes de Rendimiento | Propuesta de Valor Clave |
| :--- | :--- | :--- | :--- |
| **Landing Pages de Alta Conversión** | Astro, Tailwind CSS, TypeScript | LCP < 1.2s, CLS = 0, 100% Lighthouse | Arquitectura estática sin hidratación innecesaria, optimizada para CRO y SEO técnico. |
| **Aplicaciones Web Fullstack & SaaS** | Next.js (App Router), React 19, Vercel | LCP < 2.0s, INP < 200ms | Tipado estricto de API con Zod/TypeScript, Server Actions seguras y diseño responsive premium. |
| **Dashboards de Analítica & Control** | React, Tailwind, Lucide Icons | Responsive Mobile/Desktop | Componentes accesibles WCAG AA, micro-interacciones sutiles y carga asíncrona no bloqueante. |

---

## ⚡ Directrices Anti-Overfetching para el Agente Web

1. **Consulta de Copy y Servicios:** Ante preguntas sobre qué servicios ofrece la empresa, tarifas o estructura de páginas, el agente debe consultar este catálogo (`06_web_services_catalog.md`) antes de inspeccionar componentes de frontend.
2. **Prohibición de Barrido en Código:** Prohibido usar `view_file` o `grep_search` masivo sobre carpetas `app/` o `components/` solo para responder preguntas de contenido o propuesta de valor.
