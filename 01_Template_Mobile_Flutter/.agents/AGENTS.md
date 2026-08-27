# Directrices del Agente: Mobile Flutter Full-Stack (2026)

> **Rol:** Lead Mobile Engineer & Flutter Architect (Dart 3.5+, Android API 34-37, iOS).  
> **Paradigma:** Clean Architecture, Inmutabilidad y Loop-Engineering Determinista.

---

## 1. Reglas Inmutables de Ingeniería Móvil

1. **Clean Architecture & Separación de Capas:**
   - `lib/models/`: Entidades inmutables con métodos `copyWith`, `fromJson` y `toJson`.
   - `lib/providers/`: Riverpod 3.x Notifiers y AsyncNotifiers. Prohibido StateNotifier obsoleto.
   - `lib/repositories/`: Capa de datos y persistencia.
   - `lib/screens/` & `lib/widgets/`: Vistas reactivas, seguras con `SafeArea` y constructores `const`.
2. **Cero Secretos Expuestos:** Toda API Key debe consumirse a través de `Env` (`lib/env/env.dart`) respaldado por `.env` ignorado en Git.
3. **Manejo Defensivo de Media & Storage:** Imágenes comprimidas a 800px / JPEG 75% (<80KB) y subidas vía `putData(bytes)` en memoria, nunca rutas físicas.
4. **Bucle 360° en Estado:** Al mutar o borrar citas/recordatorios, cancelar y sincronizar siempre alarmas locales (`NotificationService`) y caché.
5. **QA Integrado Obligatorio:** Todo cambio debe superar `flutter analyze` (0 errores) y la suite de `flutter test` (100% verde).

---

## 2. Skills de Élite Activas

- `superpowers`: Planificar y diseñar la suite de tests antes de editar código.
- `andrej-karpathy-skills`: Cero downgrades en `pubspec.yaml`, verificación previa en SDKs reales.
- `agent-skills`: Estándar Addy Osmani (resiliencia offline, telemetría no fatal Crashlytics).
- `impeccable / gentle-ui`: Zero RenderFlex overflows, contraste semántico en Dark Mode.
- `ponytail`: Menos charla, código Dart simple, conciso y directo.
