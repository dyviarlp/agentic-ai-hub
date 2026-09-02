# Hardening de Infraestructura Cloud & Firebase (Cloud Rules Hardening)

> **Dominio:** `cloud_rules_hardening` (04)  
> **Propósito:** Reglas inmutables y patrones de auditoría estática para Cloud Firestore, Cloud Storage, Vercel Edge y API Gateways.  
> **Última validación:** 2026-09-02  
> **Normativa:** Firebase Security Best Practices 2026 & OWASP Cloud Top 10.

---

## 1. Anti-Patrones Críticos en `firestore.rules`

Los siguientes patrones representan fallos críticos de seguridad y son causa de rechazo inmediato:

1. **Acceso Universal No Autenticado:**

   ```javascript
   // ❌ CRÍTICO: Base de datos pública
   match /{document=**} {
     allow read, write: if true;
   }
   ```

2. **Acceso Autenticado sin Control de Propiedad (BOLA):**

   ```javascript
   // ❌ CRÍTICO: Cualquier usuario logueado accede a datos de cualquier otro usuario
   match /users/{userId}/{allPaths=**} {
     allow read, write: if request.auth != null;
   }
   ```

3. **Escritura sin Validación de Campos / Tipos:**

   ```javascript
   // ❌ ALTO: Permite inyección de roles (ej. role: "admin") o escalada de privilegios
   match /users/{userId} {
     allow write: if request.auth.uid == userId;
     // Falta validar que request.resource.data.role no sea alterado por el cliente
   }
   ```

---

## 2. Regla Canónica de Hardening para Firestore

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Funciones Helper Globales
    function isSignedIn() {
      return request.auth != null;
    }
    function isUser(uid) {
      return isSignedIn() && request.auth.uid == uid;
    }
    function notUpdating(field) {
      return !(field in request.resource.data) || resource.data[field] == request.resource.data[field];
    }

    // Default deny
    match /{document=**} {
      allow read, write: if false;
    }

    // Regla de usuario con inmutabilidad de roles
    match /users/{userId} {
      allow read: if isUser(userId);
      allow create: if isUser(userId) && request.resource.data.role == 'user';
      allow update: if isUser(userId) && notUpdating('role');
    }
  }
}
```

---

## 3. Hardening de Cloud Storage (`storage.rules`)

- Limitar el tamaño máximo de subida (`request.resource.size < 5 * 1024 * 1024` para 5MB).
- Validar tipos MIME (`request.resource.contentType.matches('image/.*')`).
- Restringir la ruta al UID del propietario (`match /users/{userId}/{fileName}`).

---

## 4. Auditoría de Cabeceras CORS en Vercel

- Prohibir `Access-Control-Allow-Origin: *` cuando `Access-Control-Allow-Credentials: true`.
- Forzar encabezados HSTS, X-Content-Type-Options: nosniff, X-Frame-Options: DENY y Content-Security-Policy restrictivo.
