---
name: typescript-safety
description: Directrices de tipado estricto, contratos inmutables, validación defensiva en runtime con Zod y cero dynamic/any en TypeScript.
---

# TypeScript Safety: Tipado Estricto y Contratos Inmutables (TypeScript 5.x+)

> **Nivel de Activación:** Nivel 0 (Fondo Inmutable - Siempre Activo).  
> **Objetivo:** Eliminar errores de tipo en tiempo de ejecución (`TypeError`, `undefined is not a function`), estados inconsistentes y fugas de datos.

---

## 1. Reglas Inmutables de Tipado

1. **Cero `any` o Casts Forzados (`as T`):**
   - Prohibido usar `any` en funciones, propiedades o retornos. Usar `unknown` con type guards o esquemas de validación.
   - Prohibido el uso de `as SpecificType` sin haber realizado una comprobación previa mediante `instanceof`, `typeof` o un validador Zod.
2. **Inmutabilidad y Modificadores `readonly`:**
   - Tipar propiedades inmutables con `readonly` y colecciones con `ReadonlyArray<T>` o `as const`.
   - Evitar mutaciones directas de arrays u objetos en el estado de React; usar actualizaciones puras inmutables.
3. **Uniones Discriminadas Exhaustivas:**
   - Modelar estados de UI y respuestas de red mediante Discriminated Unions con un campo literal discriminador (ej. `kind` o `status`).
   - Usar comprobaciones exhaustivas con tipo `never` en bloques `switch`:

     ```ts
     function assertNever(x: never): never {
       throw new Error(`Unexpected object: ${JSON.stringify(x)}`);
     }
     ```

---

## 2. Validación Defensiva en Fronteras (Zod)

- Toda entrada externa (solicitudes HTTP, variables de entorno `process.env`, datos leídos de LocalStorage o APIs de terceros) debe validarse con esquemas Zod antes de acceder a sus propiedades internas.
- Parsear con `schema.safeParse(data)` para un manejo elegante de errores sin lanzar excepciones incontroladas.
