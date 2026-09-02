# Memoria de Dominio 05: Despliegue en Vercel, Cache e Invariantes CI/CD (2026)

> **Última validación:** 2026-09-02  
> **Ámbito:** Vercel deployment, Serverless Edge, variables de entorno y compuertas de calidad automatizadas.

---

## 🚀 Despliegue y Vercel Edge Runtime

1. **Estrategias de Caché y Revalidación:**
   - Para páginas dinámicas con actualización periódica: usar **ISR (Incremental Static Regeneration)** con `export const revalidate = 3600`.
   - Para assets estáticos: `Cache-Control: public, max-age=31536000, immutable`.
   - Para APIs con datos dinámicos: `Cache-Control: s-maxage=60, stale-while-revalidate=600`.
2. **Seguridad en Variables de Entorno:**
   - Prohibido versionar archivos `.env` o credenciales en git. Mantener siempre `.env.example` sincronizado.
   - Restringir el prefijo `NEXT_PUBLIC_` o `PUBLIC_` estrictamente a variables que deban exponerse en el bundle cliente.

---

## 🛡️ Compuertas de Calidad Pre-Commit (Evidence Gates)

Antes de fusionar código o desplegar a producción, todo proyecto debe superar sin advertencias:

```bash
# 1. Análisis estático y linter
npm run lint

# 2. Batería de pruebas unitarias y de integración
npm test

# 3. Compilación limpia y análisis de bundle
npm run build
```

- **Invariante Zero-Warnings:** Cualquier advertencia de compilador o linter es tratada como un fallo bloqueante.
- **Rollback Instantáneo:** Garantizar que los despliegues en Vercel generen enlaces de previsualización (*Preview Deployments*) inmutables antes de la promoción a producción.
