# ConteoVerde V9 — Dictado con pausa y Sumar Conteos

Aplicación web estática de inventarios para **GitHub Pages**. Funciona con un solo `index.html`, sin servidor y sin enviar inventarios ni archivos de Merch a un servicio externo.

## Cambios de V9

### 1. Dictado: pausa después de «SAP»

En **Finalizar inventario → Dictado → Iniciar dictado**, el sistema pronuncia primero **«SAP»**, espera **1.15 segundos desde que termina de decir esa palabra** y luego empieza a dictar los dígitos del código uno por uno. Esto también se aplica al pasar al siguiente artículo.

Puedes pausar, reanudar, repetir, retroceder y avanzar. Si pausas durante el silencio, el código no se reproduce hasta reanudar. Continúa leyendo una palabra clave del producto, la cantidad en piezas y la cantidad en KG, L u otra unidad cuando corresponda. Mantiene la vista previa del mismo PDF.

En **Estilo de voz** puedes elegir **Asistente grave** (predeterminado) o **Natural**. El primero selecciona preferentemente voces masculinas de español cuando están instaladas y ajusta un poco el tono y la velocidad. **No es la voz oficial de Jarvis**, y la calidad exacta depende del navegador, del sistema operativo y de sus voces de español disponibles. Usa Chrome o Edge actualizados para mayor compatibilidad.

### 2. Sumar Conteos de dos o más personas

Se agregó una **cuarta opción «Sumar Conteos»** dentro de **Finalizar inventario → Descargar reporte**. También se puede abrir desde el botón **Σ Sumar Conteos** en la barra superior, incluso sin haber cargado un catálogo; por ejemplo, desde el equipo del gerente que recibe los conteos.

**Procedimiento recomendado:**

1. Cada persona realiza su conteo por separado en ConteoVerde y exporta su reporte final en **Excel (.xlsx)**.
2. En el equipo que realizará la consolidación, abre **Σ Sumar Conteos**.
3. Selecciona **dos o más** archivos Excel exportados por ConteoVerde; puedes cargar hasta 30 archivos de 20 MB cada uno.
4. Haz clic en **Σ Sumar reportes seleccionados**. Verás el número de reportes, los artículos encontrados y los productos con conteo.
5. Elige **Excel unificado**, **PDF unificado** o **Dictado del total**. Si prefieres que no aparezcan artículos en cero, desmarca la casilla correspondiente.

**Cómo se suman los productos:** se comparan el **SAP** y la **descripción** del artículo; también se verifica la unidad. Se suman únicamente cantidades de la misma unidad. Las piezas se mantienen separadas de KG/L, sin conversiones. Los productos que solo aparecen en un archivo también se conservan. Si un SAP aparece con nombres diferentes, el sistema los deja separados y muestra una advertencia para revisión, en lugar de mezclarlos sin autorización. Si los archivos indican unidades incompatibles para el mismo producto (p. ej., KG y L), se cancela la suma y aparece una explicación.

**Protecciones:**

- Rechaza archivos repetidos con contenido idéntico para evitar sumar dos veces el mismo reporte.
- Solo admite **reportes finales .xlsx de ConteoVerde**, no el catálogo de inventario original o reportes arbitrarios. Primero hay que generar el Excel desde cada dispositivo.
- No cambia los conteos de la sesión activa ni reinicia el catálogo o la lista Merch.
- No guardes otra vez como reporte de un participante un archivo consolidado, y **no mezcles un consolidado con sus archivos originales**, porque duplicarías conteos. Para corregir una suma, selecciona nuevamente todos los archivos individuales actualizados.
- La consolidación se realiza en la memoria del navegador, sin sincronización automática entre personas.

### 3. Formatos de exportación y compatibilidad

- En Excel: conserva **Familia | SAP | Producto Descripción | Piezas | Cant. Unid | Unidad | Registros**. Las columnas Piezas, Cant. Unid y Unidad permanecen centradas. En un consolidado, también se suman las cifras de la columna Registros.
- En PDF: usa los mismos totales y el mismo orden de columnas, con identificación de reporte consolidado.
- En Dictado: utiliza el PDF consolidado y pronuncia los totales finales; no lee por separado cada uno de los reportes originales.
- Se probaron los `.xlsx` con lectura automática de hojas de cálculo y los PDF con un lector de PDF. La comprobación en la instalación específica de Microsoft Excel de cada tienda sigue siendo recomendable.

## Funciones de versiones anteriores que se conservan

- Carga de catálogos de inventario `.xls` y `.xlsx` (incluidos el formato SAP anterior y el catálogo con 262 artículos).
- Búsqueda por descripción, **SAP y SKU POS** (cuando se cargan equivalencias Merch).
- Actualización de la lista Merch mediante PDF/Excel/CSV. Tras validar el archivo pide confirmar el reinicio del conteo local; si la carga falla o se cancela, conserva los datos previos.
- Conteo en piezas por defecto, con opción de KG/L, botones **Sumar** y **Restar**, historial y deshacer.
- Botones rápidos +1, +5, +10 y botón de **pick pack** para descripciones como `CJ1000PZA`.
- Exportación individual a Excel, PDF o Dictado.

## Actualizar GitHub Pages

1. Descomprime el ZIP y entra a la carpeta `ConteoVerde_V9_GitHub`.
2. Reemplaza el archivo `index.html` de tu repositorio por el nuevo. No necesitas otro repositorio.
3. Conserva `.nojekyll` si ya lo usabas.
4. Confirma los cambios en la rama de publicación de GitHub Pages.
5. Recarga la aplicación con **Ctrl + Shift + R** y verifica que aparezca **«V9 · SUMAR CONTEOS + VOZ»**.

La lista Merch no está embebida en el paquete. Las equivalencias se guardan en el navegador local donde las cargas. La aplicación publicada es de acceso público si el repositorio/sitio lo es; no utilices GitHub Pages como almacén privado de información confidencial.

**Archivos:** `index.html` (aplicación completa), `.nojekyll` (compatibilidad GitHub Pages), `README.md` (guía) y `LICENCIA-JSZip.txt` (licencia de biblioteca de Excel integrada).
