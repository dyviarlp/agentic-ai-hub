---
name: modern-web-guidance
description: Guía de estándares web 2026, APIs nativas del navegador, Zero-JS bloat y soluciones CSS-first para máximo rendimiento y ligereza.
---

# Modern Web Guidance: Estándares Web y Enfoque CSS-First (2026)

> **Nivel de Activación:** Nivel 1 (Arquitectura Frontend y Selección de Tecnologías).  
> **Objetivo:** Resolver interacciones con capacidades nativas de la plataforma web, reduciendo al mínimo el código JavaScript del cliente (*Zero-JS Bloat*).

---

## 1. La Regla de Oro: Plataforma Nativa Primero

Antes de importar cualquier librería externa o escribir código JavaScript para interactividad, agotar las siguientes capacidades nativas:

1. **Popovers y Tooltips:**
   - Usar el atributo nativo `popover` y `popovertarget` en HTML para ventanas emergentes sin JS.
2. **Ventanas Modales y Diálogos:**
   - Usar el elemento nativo `<dialog>` con `.showModal()`. Gestiona automáticamente el foco, accesibilidad y cierre con `ESC`.
3. **Acordeones y Desplegables:**
   - Usar `<details name="accordion-group">` con `<summary>` nativo.
4. **Validación de Formularios:**
   - Usar pseudo-clases CSS `:user-valid` y `:user-invalid` para retroalimentación visual inmediata tras interacción del usuario.

---

## 2. Técnicas Avanzadas de CSS Moderno

- **Selector Relacional `:has()`:**
  - Estilar ancestros o hermanos en base al estado de un hijo (ej. `form:has(:invalid) button[type="submit"] { opacity: 0.5; }`).
- **Container Queries (`@container`):**
  - Diseñar componentes desacoplados de la resolución global de pantalla mediante `container-type: inline-size`.
- **View Transitions API:**
  - Animaciones de cambio de página o estado fluidas con `document.startViewTransition()` sin frameworks pesados.
- **Scroll-Driven Animations:**
  - Controlar animaciones basadas en el progreso de desplazamiento puramente en CSS con `animation-timeline: scroll()` o `view()`.
