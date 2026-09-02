---
name: security-and-hardening
description: Auditoría rigurosa de reglas de seguridad en Cloud Firestore y Storage, cabeceras CORS en Vercel y cumplimiento OWASP MASVS v2.0 con ofuscación R8 en clientes móviles.
---

# Security & Hardening Evaluator (Cloud & MASVS)

Esta skill proporciona los métodos de inspección estática, análisis de configuración y auditoría de ciberseguridad para servicios Cloud (Firebase, Vercel) y aplicaciones móviles (Android/Flutter).

---

## 1. Áreas de Verificación

### A. Cloud Firestore (`firestore.rules`)

1. **Deny por Defecto:** Toda base de datos debe declarar un bloqueo raíz explícito:

   ```javascript
   match /{document=**} { allow read, write: if false; }
   ```

2. **Control de Acceso Granular (BOLA):**
   - Prohibido `allow read, write: if request.auth != null;` en colecciones que contengan datos privados de usuarios.
   - Forzar validación de pertenencia: `request.auth.uid == resource.data.userId` o `request.auth.uid == userId`.
3. **Validación de Integridad de Esquemas:**
   - Comprobar tipos de datos, longitud de strings y que campos críticos de auditoría (`createdAt`, `userId`) no sean alterados.

### B. Cloud Storage (`storage.rules`)

1. Restricción obligatoria de tamaño de archivos (`request.resource.size < N * 1024 * 1024`).
2. Validación estricta de Content-Type (`request.resource.contentType.matches('image/(jpeg|png|webp)')`).
3. Confinamiento de rutas por UID del usuario.

### C. Cabeceras HTTP y CORS en Vercel

1. Prohibir `Access-Control-Allow-Origin: *` cuando `Access-Control-Allow-Credentials: true`.
2. Obligatoriedad de cabeceras de endurecimiento:
   - `X-Content-Type-Options: nosniff`
   - `X-Frame-Options: DENY`
   - `Strict-Transport-Security: max-age=63072000; includeSubDomains; preload`

### D. OWASP MASVS v2.0 & Ofuscación R8 (Android)

1. **MASVS-CODE:** `isMinifyEnabled = true` y `isShrinkResources = true` obligatorios en `buildTypes.release`.
2. **MASVS-STORAGE:** Almacenamiento exclusivo en `EncryptedSharedPreferences` / `flutter_secure_storage`. Cero secretos en texto plano.
3. **MASVS-NETWORK:** Prohibido el tráfico HTTP sin cifrar (`cleartextTrafficPermitted="false"`).

---

## 2. Metodología de Auditoría

1. Analizar archivos de configuración (`firestore.rules`, `storage.rules`, `vercel.json`, `build.gradle`).
2. Identificar anti-patrones mediante escáner estático (`scripts/check_firestore_rules.py` y `scripts/check_masvs_mobile.py`).
3. Asignar puntuación cuantitativa (Safety Score de 0% a 100%).
4. Si se identifican vulnerabilidades críticas (`CRITICAL`), emitir veredicto **FAIL (Rechazo)** y registrar en `.agents/memory/01_vulnerabilities_registry.md`.
