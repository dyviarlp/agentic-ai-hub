# Ficha Técnica: Compilación Determinista Playwright PDF

> Última validación: 2026-09-02  
> Dominio: Headless PDF Rendering & Layout Engine

## 1. Invariantes de Maquetación (2 Páginas A4)

1. **Dimensiones:** `size: A4; margin: 0;` en CSS `@page`. Contenedores con `width: 210mm; height: 297mm; box-sizing: border-box;`.
2. **Control de Saltos:** `page-break-after: always; break-after: page;` entre páginas.
3. **Control Anti-Clipping:** El uso de `overflow: hidden` previene la aparición de una tercera página blanca pero puede silenciar texto cortado. Siempre validar con `fitz` que el texto final se encuentre en el stream extraído.

## 2. Pipeline de Generación Headless

```python
async with async_playwright() as p:
    browser = await p.chromium.launch(headless=True)
    page = await browser.new_page()
    await page.set_content(html, wait_until='networkidle')
    await page.pdf(path=output_path, format='A4', print_background=True, margin={'top': '0mm', 'right': '0mm', 'bottom': '0mm', 'left': '0mm'})
    await browser.close()
```
