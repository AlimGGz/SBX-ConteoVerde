# ConteoVerde V11 — Pausa configurable entre artículos

Esta versión mantiene todas las funciones de ConteoVerde V10: inventario XLS/XLSX, búsqueda SAP y SKU POS con Merch, suma/resta, pick pack, cronómetro, Excel/PDF, dictado y la consolidación **Sumar Conteos**.

## Novedad de Dictado

En **Finalizar inventario → Dictado** (o desde **Sumar Conteos → Dictado del total**) encontrarás **Espera entre artículos**. Puedes elegir **1, 2, 3, 4 o 5 segundos**; la configuración inicial es de **2 segundos**.

La espera ocurre **después de que termina de pronunciar las cantidades de un producto y antes de decir “SAP” del producto siguiente**. La pausa interna entre decir “SAP” y comenzar a leer su código continúa siendo **1.15 segundos**, independientemente de la espera seleccionada. La selección de 1 a 5 segundos se guarda en el navegador para futuras sesiones.

La opción se puede cambiar durante una sesión; el nuevo valor se usará a partir del siguiente intervalo que se programe. Al **Pausar**, también se detiene la espera y se conserva el tiempo restante; al **Continuar**, la espera se reanuda. **Anterior** y **Siguiente** saltan directamente al artículo elegido y cancelan cualquier espera pendiente.

No se aplica una pausa adicional después del último producto. La voz continúa seleccionándose automáticamente, sin selector manual. Conserva tres palabras consecutivas del producto y las cantidades en piezas y, cuando proceda, KG/L.

## Publicación en GitHub Pages

1. Descarga el ZIP de ConteoVerde V11.
2. Sustituye `index.html` en tu repositorio de GitHub por el archivo nuevo. Los demás archivos del ZIP son complementarios.
3. Espera la publicación de GitHub Pages y recarga con **Ctrl + Shift + R**.
4. Confirma que aparezca `V11 · DICTADO CON PAUSAS`.

Los conteos y la lista Merch permanecen en el almacenamiento de ese navegador. No se incorpora la lista Merch al código público. La calidad y disponibilidad de voz dependen del navegador y del dispositivo.
