---
name: gsap-motion
description: Animaciones cinéticas fluidas a 60/120fps, micro-interacciones de alta fidelidad con GSAP/Motion y prevención de layout thrashing.
---

# GSAP Motion: Animaciones Cinéticas y Rendimiento Visual (60/120fps)

> **Nivel de Activación:** Nivel 3 (Fase de Pulido Visual y Micro-interacciones).  
> **Objetivo:** Orquestar transiciones cinéticas fluidas y experiencias interactivas memorables sin degradar el hilo principal ni provocar saltos de layout.

---

## 1. Principios de Rendimiento en Animaciones

1. **Aceleración por GPU Exclusiva:**
   - Animar ÚNICAMENTE propiedades componibles por la GPU: `transform` (`x`, `y`, `scale`, `rotation`) y `opacity`.
   - Prohibido animar propiedades que disparan *Layout* o *Paint* costosos: `width`, `height`, `top`, `left`, `margin`, `padding` o `box-shadow`.
   - Declarar `will-change: transform` solo durante la animación y retirarlo al completarla si el elemento permanece en pantalla.

2. **Limpieza Rigurosa de Contexto en React (`gsap.context()`):**
   - Envolver toda animación GSAP en componentes React dentro de `gsap.context()` para asegurar la eliminación de timelines y observadores de scroll al desmontar el componente:

     ```tsx
     import { useEffect, useRef } from 'react';
     import gsap from 'gsap';

     export function AnimatedCard({ children }: { children: React.ReactNode }) {
       const cardRef = useRef<HTMLDivElement>(null);

       useEffect(() => {
         const ctx = gsap.context(() => {
           gsap.from(cardRef.current, {
             opacity: 0,
             y: 20,
             duration: 0.6,
             ease: 'power3.out',
           });
         }, cardRef);

         return () => ctx.revert(); // Limpieza garantizada
       }, []);

       return <div ref={cardRef}>{children}</div>;
     }
     ```

---

## 2. Orquestación y ScrollTrigger

- **ScrollTrigger sin Bloqueos:**
  - Evitar cálculos síncronos pesados dentro de callbacks `onUpdate` de ScrollTrigger.
  - Usar `scrub: 1` para suavizado inercial en efectos de revelación por desplazamiento.
- **Micro-interacciones Táctiles:**
  - Utilizar amortiguación elástica en clics y hovers para proporcionar una sensación física táctil premium.
