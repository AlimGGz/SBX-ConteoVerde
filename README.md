# ConteoVerde V12 — Corrección del lector Merch C1/C2

## Problema corregido

El lector de PDF de V11 identificaba **Código SAP** y **SKU POS** usando coordenadas fijas de las columnas del formato C1. El PDF **Lista de Precios Merch XMAS 2026_WK 45 C2 1 (1).pdf** tiene una distribución distinta: los dos códigos se encuentran más a la derecha y el documento tiene 24 páginas (incluidas páginas de precios). Por eso, V11 daba el mensaje de que no encontraba códigos SAP o SKU POS.

En V12 el lector detecta las posiciones de las columnas por sus encabezados dentro del PDF y utiliza ese diseño en las siguientes páginas. Omite las páginas que solo incluyen precios y no mezcla información de precios con el catálogo de búsqueda.

## Pruebas realizadas

- Lista Merch C1 anterior: **341 equivalencias SAP–SKU POS** importadas correctamente.
- Lista Merch C2 aportada: **341 equivalencias SAP–SKU POS** importadas correctamente.
- Inventario `ReporteInventario_NP2893.xls`: **285 productos** importados.
- Búsqueda de SKU POS `50737` con ese inventario: localiza SAP `154150`.
- Un inventario con un producto contado se reinicia después de confirmar la actualización Merch.
- Un PDF inválido no reemplaza el catálogo Merch cargado ni borra conteos.
- No hay errores JavaScript en la prueba automatizada de navegador.

## Cómo instalar la actualización en GitHub Pages

1. Descarga el ZIP V12 y extrae su contenido.
2. En el repositorio que ya aloja ConteoVerde, reemplaza `index.html` por el nuevo archivo.
3. Confirma el cambio y recarga GitHub Pages con **Ctrl + Shift + R**.
4. Verifica que se muestre **V12 · LECTOR MERCH C1/C2**.
5. Haz clic en **Actualizar lista Merch** y selecciona el PDF de C2.
6. Revisa las equivalencias detectadas; **antes de confirmar**, exporta cualquier conteo activo que quieras conservar. La actualización sí reinicia los conteos, por diseño.
7. Confirma la actualización solo si quieres iniciar un conteo desde cero.

### Seguridad y datos

- Los datos del PDF se procesan en el navegador y las equivalencias se guardan en el almacenamiento local del dispositivo. No se adjunta el PDF a la distribución de GitHub.
- El catálogo Merch se usa exclusivamente como equivalencia de búsqueda y **no agrega productos que no existan en el Excel de inventario cargado**.
- Esta versión mantiene las funciones de ConteoVerde V11: sumar/restar, pick pack, cronómetro, dictado con pausas de 1 a 5 segundos, Excel/PDF y Sumar Conteos.
- La lista de Merch contiene información interna; no publiques el PDF original ni las equivalencias en un repositorio público.
