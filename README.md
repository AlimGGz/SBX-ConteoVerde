# ConteoVerde V8 — Inventario, Merch semanal, pick pack y Dictado

Aplicación estática para **GitHub Pages**, compatible con computadoras, tabletas y teléfonos. Funciona con un único archivo `index.html`, sin servidor propio ni bases de datos. La información se procesa en el navegador.

## Cambios de la V8

### 1. Actualizar lista Merch desde la aplicación

- Presiona **Actualizar lista Merch** en la barra superior.
- Selecciona el PDF semanal que contiene las columnas **Código SAP** y **SKU POS**, o una lista equivalente en **.xlsx, .xls o .csv**.
- La aplicación procesa el documento y muestra cuántas equivalencias identificó. **No publica ni muestra una lista independiente de mercancía**, no carga precios y no añade productos que no estén en el Excel de inventario.
- Solo cuando la lectura tenga éxito se solicita la confirmación del cambio. **Al confirmar, se reinician a cero todos los conteos y se borra el historial del inventario actual.** Si cancelas o el archivo no se puede leer, el conteo actual y la lista Merch anterior se conservan.
- La nueva correspondencia se guarda en el almacenamiento local del navegador de ese dispositivo. **Si abres la página en otro navegador, equipo, modo incógnito o borras los datos del sitio, tendrás que volver a cargar la lista.**
- El importador PDF está probado con el formato del documento **Lista de Precios Merch XMAS 2026_WK 45 C1.pdf**, del que recuperó **341 relaciones** entre SAP y SKU POS. Otros diseños de PDF podrían requerir adaptación. Si un PDF no se reconoce, es preferible cargar la misma lista como Excel con esas dos columnas.

### 2. Compatibilidad de Excel

- Acepta el inventario original de 262 productos (`lista.xlsx`) y `ReporteInventario_NP2893.xls` de 285 SAP únicos.
- Se corrigió el orden de elementos `autoFilter` y `mergeCells` en el XML de la hoja exportada; el orden anterior podía provocar que Microsoft Excel solicitara reparar el archivo.
- Se conserva el orden de columnas **Piezas, Cant. Unid, Unidad**, con esas columnas centradas. Se conservan SAP y descripción, así como las cantidades numéricas.
- Se comprobó que los `.xlsx` exportados contienen ZIP/XML válido y pueden volver a abrirse mediante un lector de hojas de cálculo. **No sustituye una prueba en tu instalación concreta de Microsoft Excel**, que no está disponible en este entorno.

### 3. Botón de pick pack

- El nombre/descripción del inventario se analiza en busca de patrones como **`CJ 1000 PZA`, `CJ1000PZAS`, `CJ52PZA`**.
- Si existe un pack válido, se añade un botón **`+ 1 CJ (1,000 pzas)`**, además de `+1`, `+5` y `+10`.
- Cada clic añade la cantidad exacta de piezas indicada para **una caja**, sin cambiar la unidad del producto ni convertir cantidades que el usuario registra en KG/L.
- Las operaciones quedan registradas en el historial y pueden deshacerse. No se permite restar más que lo contado.

### 4. Modo Dictado

- Haz clic en **Finalizar inventario**, elige **Dictado** y presiona **Generar y descargar reporte**.
- Se abrirá el **mismo PDF que la opción de exportar PDF**, con controles de lectura en el panel lateral.
- Pulsa **Iniciar dictado**. Se pronuncia el **SAP dígito por dígito**, **una palabra clave del producto**, las **piezas contadas** y, cuando haya cantidades registradas, los **KG, L u otra unidad del Excel** por separado.
- Incluye **Pausar / Continuar**, **Anterior**, **Siguiente**, control de velocidad, **Descargar PDF** y **Abrir PDF en otra pestaña**.
- Si la casilla **Incluir productos sin conteo** está marcada, los artículos en cero estarán tanto en el PDF como en el dictado. Desmárcala antes de generar si quieres leer solo los contados.
- Usa la función de voz del navegador; funciona mejor en **Google Chrome o Microsoft Edge actualizados** y requiere un dispositivo con salida de audio y voces disponibles. No se crea un archivo de audio.
- El orden del dictado corresponde al orden de los productos del PDF. El nombre completo también aparece en el panel lateral.

## Publicar en GitHub Pages

1. Descarga el archivo ZIP de esta versión y descomprímelo.
2. En tu repositorio de GitHub Pages, reemplaza el archivo **`index.html`** anterior por el nuevo de la carpeta.
3. Incluye el archivo `.nojekyll` si es necesario. `README.md` y la licencia son documentos de apoyo.
4. Publica los cambios. Si GitHub Pages no estaba habilitado, ve a **Settings > Pages > Deploy from a branch > main > /(root)**.
5. Recarga la página con **Ctrl + Shift + R** para ver la etiqueta **`V8 · MERCH + PICK PACK + DICTADO`**.
6. Carga el Excel de inventario como siempre, y carga el PDF de Merch por el botón **Actualizar lista Merch**. Puedes cargar Merch antes o después del inventario, pero **subir una nueva versión de Merch reiniciará los conteos activos al confirmar**.

## Seguridad y respaldo

- El PDF de Merch **no va dentro del ZIP ni dentro del código** publicado. La lista se procesa directamente en el navegador y únicamente sus equivalencias de códigos se conservan localmente.
- Una página pública de GitHub Pages no requiere iniciar sesión; **cualquier persona con el enlace puede abrir la aplicación**, aunque no verá automáticamente el catálogo Merch de tu dispositivo.
- El almacenamiento local no es una base de datos compartida ni un mecanismo de cifrado. Quien tenga acceso al mismo navegador/perfil podría examinar sus datos guardados.
- **Exporta el inventario antes de actualizar Merch**, porque el reinicio posterior a la confirmación es definitivo.
- Para un catálogo central verdaderamente privado, compartido entre tiendas o con permisos por usuario, se necesitaría una solución de servidor con autenticación.

## Archivos del paquete

- `index.html`: aplicación completa con lectores XLS/XLSX, PDF Merch del formato probado, generador PDF, Excel y síntesis de voz.
- `.nojekyll`: configuración de publicación estática para GitHub Pages.
- `README.md`: guía de uso y publicación.
- `LICENCIA-JSZip.txt`: atribución de la librería JSZip integrada.
