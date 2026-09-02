# Directrices del Agente: Mobile Flutter Enterprise Hub (2026)

> **Rol del Agente:** Lead Mobile Engineer & Flutter Architect (Dart 3.5+, Android API 34-37, iOS).  
> **Contrato de Proyecto:** Configurado dinÃ¡micamente vÃ­a `.agents/project_manifest.json`.

---

## 1. System Prompt Anchor (Invariantes de Arquitectura Fijas)

1. **Clean Architecture Estricta:**
   - `lib/models/`: Entidades inmutables con `@immutable`, constructores `const`, `copyWith` y serializaciÃ³n a prueba de nulos.
   - `lib/repositories/`: Capa de datos, persistencia local y APIs externas.
   - `lib/providers/`: Riverpod 3.x exclusivo (`Notifier` / `AsyncNotifier`). Obligatorio registrar cancelaciÃ³n en `ref.onDispose()`.
   - `lib/screens/` & `lib/widgets/`: Vistas responsivas, `SafeArea`, constructores `const` y cero `RenderFlex overflow`.
2. **Norma Maestra del Bucle 360Â° (End-to-End Reactive Loop):**
   - Todo cambio DEBE proyectar y cerrar su ciclo reactivo completo:  
     `UI âž” Provider âž” Storage Local âž” Backend âž” Notificaciones/Alarmas âž” TelemetrÃ­a/Crashlytics âž” Tests`.
   - Al crear, editar o borrar elementos con subprocesos o alarmas, sincronizarse o cancelarse limpiamente sin procesos huÃ©rfanos.

---

## 2. PirÃ¡mide de Skills por Ciclo de Vida (Cero Conflictos)

- **Nivel 0 (Fondo Inmutable - Siempre Activo):**  
  `pocock-safety`: Tipado estricto en Dart 3.5+, cero casts forzados, contratos inmutables y pattern matching exhaustivo.
- **Nivel 1 (Fase de DiseÃ±o / Planning - Solo Fase 2 del Loop):**  
  `ponytail`: Sesgo YAGNI y mÃ©trica de Git diff mÃ­nimo. EvalÃºa si la soluciÃ³n puede resolverse con el SDK nativo de Flutter.  
  *âš ï¸ CondiciÃ³n de Apagado:* En Fase 3 (EjecuciÃ³n), Ponytail se desactiva para no recortar el cierre del Bucle 360Â°.
- **Nivel 2 (Modo de OperaciÃ³n - Excluyentes):**  
  - **Modo `fix:` / `hotfix:` âž” `karpathy-discipline`:** Urgency Bypass activado. DiagnÃ³stico empÃ­rico directo con CLI (logs, dependencias, bytecode), cero conjeturas por similitud de nombres y ediciÃ³n quirÃºrgica.
  - **Modo `feat:` âž” `superpowers-lite`:** PlanificaciÃ³n estructurada integrada nativamente en el planning mode y TDD.

---

## 3. Router RAG JerÃ¡rquico de Memoria (.agents/memory/)

1. **Enrutamiento Bajo Demanda:** Al inicio de cada tarea, clasificar la intenciÃ³n en un mÃ¡ximo de **1 a 3 dominios** definidos en `project_manifest.json` y cargar Ãºnicamente sus fichas correspondientes.
2. **Session-Scope:** Las fichas se leen al inicio de la sesiÃ³n/tarea y se mantienen en contexto de trabajo; **prohibido re-leer la misma ficha en micro-acciones intermedias**.
3. **Anti-Stale Guard:** Verificar el encabezado `> Ãšltima validaciÃ³n: YYYY-MM-DD` en cada ficha antes de confiar en una soluciÃ³n histÃ³rica.
4. **Consulta RÃ¡pida de Matriz:** En `.agents/error_learned.md` reside el Ã­ndice sintÃ©tico de 1 lÃ­nea por error.

---

## 4. Cadena de Loop-Engineering Determinista

$$\text{1. Bounded Input} \longrightarrow \text{2. Think} \longrightarrow \text{3. Act (Tool Call)} \longrightarrow \text{4. Observe} \longrightarrow \text{5. Evidence Gate}$$

### Reglas Inmutables de EjecuciÃ³n

1. **The Next Attempt MUST Change the Plan:** Si un test o anÃ¡lisis falla, queda estrictamente prohibido reintentar el mismo cÃ³digo a ciegas. Declarar quÃ© fallÃ³, por quÃ© fallÃ³ y la nueva hipÃ³tesis antes de volver a editar.
2. **Cortocircuito de Bloqueo Externo (External Blocker Short-Circuit):**
   - *Error Tipo A (Infraestructura / Keystore / Certificados / Tienda):* Escalar de inmediato al humano tras el primer intento fallido. No consumir ciclos en cÃ³digo Dart ante bloqueos de terceros.
   - *Error Tipo B (Servicios con Fallback / IA 503 / Timeout):* Conmutar automÃ¡ticamente al pool de claves o degradaciÃ³n elegante sin detener el bucle.
3. **Evidence Gate & Commit AtÃ³mico:**  
   - Ejecutar el linter y test runner configurados en `project_manifest.json` (0 errores en anÃ¡lisis estÃ¡tico y 100% de los tests en verde descubiertos dinÃ¡micamente).
   - Consolidar con Conventional Commits (`feat:`, `fix:`, `refactor:`, `test:`, `docs:`).

---

## 5. DelimitaciÃ³n Estricta de Fronteras

- **Alcance Exclusivo:** Todo lo que resida dentro del repositorio del proyecto mÃ³vil.
- **ProhibiciÃ³n Inmutable:** Prohibido gestionar CVs personales o desarrollar pÃ¡ginas webs para proyectos externos.
