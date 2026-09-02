# Memoria de Dominio 04: Almacenamiento Local, APIs & Repositorios

> Última validación: 2026-09-02 | Estado: Plantilla Oficial Enterprise Hub  
> Invariantes de persistencia local, contratos de API externos y caché tolerante a fallos.

---

## 📋 Reglas Preventivas de Dominio

1. **Contratos Inmutables:** Los repositorios deben exponer únicamente tipos inmutables del dominio, abstrayendo fuentes HTTP, Firestore o SQLite.
2. **Tolerancia a Fallos de Red:** Implementar degradación elegante y reintentos exponenciales acotados con fallback a caché local.
3. **Zero Secrets en Código:** Prohibido almacenar claves privadas o tokens en código fuente; uso estricto de variables seguras.
