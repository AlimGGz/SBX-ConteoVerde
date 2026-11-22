# ConteoVerde V16 · Unidades y dictado

## Instalación
1. Exporta cualquier inventario en curso como respaldo antes de actualizar.
2. Sustituye `index.html` en tu repositorio de GitHub Pages. No es necesario crear otro repositorio.
3. Recarga la página (Ctrl + Shift + R). Comprueba que aparezca V16 · UNIDADES Y DICTADO.

## Unidades de conteo
- SAP 149438, 149463 y 149469: PQT (un paquete por registro de una unidad). KG sigue disponible como cantidad independiente.
- Café distinto de 250 g: BOL para las presentaciones identificadas por peso o en KG; café de 250 g conserva PZA. Incluye 5 LB, 2.27 KG y 2.7 KG. No aplica a materiales de empaque.
- SAP 149746: BOL (una bolsa por unidad).
- Panqués: REB (rebanadas). +1 suma una rebanada y el botón +1 PANQUÉ suma siete. No aplica a cajas o empaques para panqué.
- No se realizan conversiones automáticas a KG o L.
- El Excel mantiene Piezas, Cant. Unid y Unidad, más Unidad conteo, que indica qué representa el primer número. En PDF las cantidades especiales llevan su etiqueta PQT, BOL o REB.

## Inventarios previos
Si hay conteos anteriores de panqué, la primera vez se pregunta si eran panqués enteros (Aceptar: ×7) o rebanadas (Cancelar: conservar). El historial se ajusta de acuerdo con esa decisión. No se modifica el conteo de otras familias. Revisa las cantidades antes de exportar. Sumar Conteos rechaza reportes antiguos con cantidades de panqué no nulas sin unidad de conteo explícita, para evitar mezclar panqués enteros y rebanadas. Reexporta esos reportes desde V16 en rebanadas.

## Dictado
Abre Finalizar inventario → Dictado. Con Audio del dictado activado se mantiene la lectura por voz y las pausas anteriores. Sin audio, el artículo visible avanza automáticamente cada 1–5 segundos según el selector de espera. Los controles de pausa, anterior, siguiente y reproducción siguen disponibles. Cambiar audio durante la reproducción reinicia el artículo actual. Si lo cambias estando en pausa, pulsa Iniciar dictado para continuar desde ese artículo.

Mientras se reproduce, la app solicita mantener la pantalla activa (Screen Wake Lock). En GitHub Pages se sirve por HTTPS; la disponibilidad depende del navegador, batería, permisos y visibilidad de la pestaña. Cuando termina o se cierra el dictado, libera la solicitud. Si el navegador no lo admite, configura el bloqueo automático desde el dispositivo.

## Interfaz
Las tarjetas de búsqueda y el detalle se ajustan al contenido, incluyendo nombres largos y cantidades grandes. Las funciones de importación XLS/XLSX, Merch, Pick Pack, historial, cronómetro, Excel/PDF y consolidación se mantienen.
