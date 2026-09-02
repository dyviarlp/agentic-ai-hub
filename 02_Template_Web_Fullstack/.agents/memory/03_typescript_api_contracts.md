# Memoria de Dominio 03: Contratos TypeScript y Vercel Serverless APIs (2026)

> **Última validación:** 2026-09-02  
> **Ámbito:** Tipado estricto, endpoints Serverless/Edge (`api/`), validación con Zod y contratos de datos.

---

## 🔒 Reglas Inmutables de Tipado

1. **Cero `any` o Casts Forzados:**
   - Prohibido terminantemente el uso de `any`. Emplear `unknown` con guardas de tipo o esquemas de validación en tiempo de ejecución.
   - Prohibido el uso de `as Type` salvo tras validación booleana exhaustiva.
2. **Discriminated Unions para Respuestas y Estados:**
   - Todo estado de carga o respuesta asíncrona debe tiparse como unión discriminada exhaustiva:

     ```ts
     type AsyncResult<T> =
       | { status: 'idle' }
       | { status: 'loading' }
       | { status: 'success'; data: T }
       | { status: 'error'; error: Error };
     ```

---

## 🌐 Endpoints Vercel Serverless & Edge Routes (`app/api/`)

1. **Validación Estricta con Zod en Fronteras:**
   - Todo payload recibido (JSON body, query parameters, route params) DEBE validarse contra un esquema Zod antes de procesar:

     ```ts
     import { z } from 'zod';
     import { NextResponse } from 'next/server';

     const ContactSchema = z.object({
       email: z.string().email(),
       name: z.string().min(2).max(100),
       message: z.string().min(10),
     });

     export async function POST(req: Request) {
       try {
         const json = await req.json();
         const data = ContactSchema.parse(json);
         // Lógica tipada con datos sanitizados...
         return NextResponse.json({ success: true, id: '...' }, { status: 200 });
       } catch (error) {
         if (error instanceof z.ZodError) {
           return NextResponse.json({ success: false, errors: error.flatten() }, { status: 400 });
         }
         return NextResponse.json({ success: false, message: 'Internal Server Error' }, { status: 500 });
       }
     }
     ```

2. **Cabeceras de Seguridad y CORS:**
   - Configurar `Access-Control-Allow-Origin` restringido a dominios conocidos.
   - Añadir cabeceras estándar: `X-Content-Type-Options: nosniff`, `X-Frame-Options: DENY`, `Referrer-Policy: strict-origin-when-cross-origin`.
