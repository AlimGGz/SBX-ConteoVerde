# ConteoVerde V13 — Pick Pack mejorado

## Qué se corrigió

Se revisaron todas las descripciones del catálogo aportado de 285 SAP únicos. La versión anterior reconocía únicamente 61 presentaciones: exigía un sufijo PZA/PZAS al final de la expresión, por lo que no reconocía los códigos seguidos de capacidades, pesos o paquetes internos.

El nuevo detector permite:
- `CJ1500` / `CJ1500PZAS` → botón `+ 1 CJ (1,500 pzas)`.
- `CJ24PZAS` / `CJ24PZAS110GR` → `+ 1 CJ (24 pzas)`.
- `CJ/1000PZAS` y `CJ 1000 PZA` → 1,000 piezas.
- `CJ12BLIST3PZAS` → 12 × 3 = **36 piezas**.
- `CJ25PQT24PZAS` → 25 × 24 = **600 piezas**.
- `C100P`, `C500P`, `C12B`, `C12BOL` → cantidades por presentación expresadas en piezas o bolsas.
- `PQT100PZAS`, `ROL500PZAS`, `BOL6PZAS`, `CHA12PZAS` → botones por paquete, rollo, bolsa o charola.

La aplicación **no convierte** piezas a kilogramos/litros. Cuando la descripción informa, por ejemplo, `CJ12LT`, muestra una advertencia en lugar de inventar una cantidad de piezas. Ante descripciones sin cantidad de empaque, permanecen disponibles la suma manual y los botones +1, +5 y +10.

## Resultados de la auditoría

Catálogo de 285 SAP: **246 presentaciones detectadas**, 38 sin un número de empaque explícito y 1 con unidad ambigua que requiere revisión manual (`CJ12LT`). Distribución: 147 con prefijo CJ, 92 con CnP/CnB/CnBOL y 7 en paquetes/rollos/bolsas/charolas.

El archivo de auditoría (`ConteoVerde_V13_Auditoria_PickPack_285_SAP.xlsx`) se entrega **por separado** y no debe subirse al repositorio, ya que contiene datos internos del inventario.

## Pruebas realizadas

- Se importó `ReporteInventario_NP2893.xls` con 285 productos SAP únicos.
- Se importó `lista.xlsx` con 262 productos.
- Se verificó en navegador el botón de `CJ1500PZAS` (1,500 piezas) y su acumulación.
- Se verificó `CJ12BLISTER3PZAS` (36 piezas), `CJ6PQT25PZAS` (150 piezas), `C100P` (100 piezas) y `CJ24PZAS` (24 piezas).
- `CJ12LT` muestra una advertencia y no añade un botón que pudiera contar piezas incorrectamente.
- No se detectaron errores JavaScript en los recorridos de prueba.

## Instalación en GitHub Pages

1. Descarga el ZIP y extrae el archivo `index.html`.
2. Sustituye el `index.html` actual de tu repositorio por el nuevo.
3. Guarda los cambios en la rama publicada.
4. Recarga el sitio publicado con **Ctrl + Shift + R**.
5. Confirma que se muestre `V13 · PICK PACK MEJORADO`.
6. Carga tu Excel de inventario. El botón de empaque aparecerá únicamente cuando la descripción permita reconocer una cantidad confiable.

**Nota:** la actualización del archivo HTML no reinicia por sí sola el inventario guardado en el mismo navegador. Importar un Excel nuevo o actualizar Merch sí puede reemplazar el inventario según las confirmaciones habituales del sistema. Exporta tu conteo antes de esos cambios.
