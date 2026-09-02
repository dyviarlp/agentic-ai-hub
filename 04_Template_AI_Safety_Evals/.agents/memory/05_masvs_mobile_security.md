# Estándar de Seguridad Móvil OWASP MASVS v2.0 (MASVS Mobile Security)

> **Dominio:** `masvs_mobile_security` (05)  
> **Propósito:** Requisitos técnicos de verificación y hardening de seguridad para clientes móviles Android y Flutter.  
> **Última validación:** 2026-09-02  
> **Referencia:** OWASP Mobile Application Security Verification Standard (MASVS) v2.0.

---

## 1. Categorías MASVS v2.0 y Controles Críticos

| Dominio MASVS | Control Clave | Verificación Técnica | Criterio de Aceptación |
| :--- | :--- | :--- | :--- |
| **MASVS-STORAGE** | Cifrado en reposo | Uso de `EncryptedSharedPreferences` / `KeyStore` / `flutter_secure_storage`. | Cero tokens o PII en texto claro en SharedPreferences/SQLite. |
| **MASVS-CRYPTO** | Criptografía robusta | Algoritmos simétricos AES-GCM (>= 256 bits) o asimétricos RSA (>= 2048) / ECC. | Prohibido DES, 3DES, RC4, MD5, SHA-1 para integridad. |
| **MASVS-AUTH** | Autenticación y sesión | Manejo seguro de tokens JWT, invalidación y biometría `BiometricPrompt`. | Biometría respaldada por CryptoObject del hardware Keystore. |
| **MASVS-NETWORK** | Seguridad en tránsito | TLS 1.3/1.2 obligatorio, Network Security Config estricto y Certificate Pinning. | Rechazar `cleartextTrafficPermitted="true"` en release. |
| **MASVS-PLATFORM** | Interacción de plataforma | Exportación mínima de Activities/Services/Receivers (`android:exported="false"`). | Todo componente expuesto debe exigir permisos explícitos de firma. |
| **MASVS-CODE** | Integridad y ofuscación | Ofuscación R8 activa (`minifyEnabled true`, `shrinkResources true`), sin logs. | Desensamblado con APKTool/JADX sin nombres de clases sensibles legibles. |

---

## 2. Directivas Obligatorias en Android

### Network Security Config (`res/xml/network_security_config.xml`)

```xml
<?xml version="1.0" encoding="utf-8"?>
<network-security-config>
    <base-config cleartextTrafficPermitted="false">
        <trust-anchors>
            <certificates src="system" />
        </trust-anchors>
    </base-config>
</network-security-config>
```

### Manifest Hardening (`AndroidManifest.xml`)

- `android:allowBackup="false"` (evitar volcado de datos vía ADB).
- `android:networkSecurityConfig="@xml/network_security_config"`.
- Desactivar `android:debuggable="false"` en compilación de producción.

---

## 3. Procedimiento de Auditoría de Compilación Móvil

1. Extraer manifiesto y recursos del paquete compilado.
2. Comprobar que no existen trazas de depuración ni símbolos internos.
3. Verificar ausencia de API keys privadas o secrets hardcodeados en binarios.
4. Generar reporte en `audit_reports/` con calificación MASVS (L1 / L2 / R).
