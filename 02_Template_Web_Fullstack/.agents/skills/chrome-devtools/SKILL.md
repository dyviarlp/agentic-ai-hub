---
name: chrome-devtools
description: Auditoría de rendimiento web, perfilado en vivo de Core Web Vitals (LCP, INP, CLS), análisis de memoria y diagnóstico de red mediante Chrome DevTools.
---

# Chrome DevTools: Diagnóstico de Rendimiento y Auditoría Web

> **Nivel de Activación:** Nivel 2 (Fase de Pruebas, Auditoría y Optimización).  
> **Objetivo:** Identificar empíricamente cuellos de botella de renderizado, tareas largas en el hilo principal y fugas de memoria antes del despliegue.

---

## 1. Auditoría de Core Web Vitals en DevTools

1. **Diagnóstico de LCP (Largest Contentful Paint):**
   - Abrir pestaña *Performance* y activar captura de capturas de pantalla (*Screenshots*).
   - Localizar el marcador `LCP` en el carril de tiempos.
   - Desglosar la cascada en 4 fases: *Time to First Byte (TTFB)*, *Resource Load Delay*, *Resource Load Duration*, y *Element Render Delay*.
   - Si el elemento LCP es una imagen o bloque de texto, asegurar carga anticipada (`preload` / `priority`).

2. **Diagnóstico de INP (Interaction to Next Paint):**
   - Filtrar el carril *Main Thread* buscando **Long Tasks** (bloques con franjas rojas > 50ms).
   - Identificar funciones JavaScript bloqueantes y desacoplarlas usando `scheduler.yield()` o `requestIdleCallback()`.

3. **Diagnóstico de CLS (Cumulative Layout Shift):**
   - Activar la casilla *Layout Shifts* en DevTools Rendering.
   - Detectar elementos que mutan de tamaño o posición sin dimensiones predefinidas.

---

## 2. Inspección de Red y Fugas de Memoria

- **Perfilado de Memoria (Heap Snapshot):**
  - Tomar instantáneas antes y después de montar/desmontar componentes complejos (modales, páginas dinámicas).
  - Verificar que no queden suscripciones activas, `addEventListener` huérfanos o timers (`setInterval`) sin limpiar en `useEffect` / `onDestroy`.
- **Throttling de Red y CPU:**
  - Validar siempre la experiencia bajo simulación de *Slow 4G* y *4x CPU Slowdown* para asegurar que el contenido esencial sea interactivo de inmediato.
