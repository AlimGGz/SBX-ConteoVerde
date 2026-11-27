# ConteoVerde V19 — Reconocimiento automático para conteos diarios

- Carga el Excel `.xls` / `.xlsx` del inventario general: la aplicación identifica automáticamente Alimentos, Leches y Vasos con reglas que combinan familia y descripción.
- En Menú > Revisar clasificación puedes ver los SAP y cambiar cualquier categoría. Los ambiguos se asignan a Revisar, nunca se incorporan automáticamente.
- En Menú > Alimentos, Leches o Vasos, crea un conteo nuevo escribiendo el responsable. Se guarda fecha y hora.
- Cada conteo nuevo guarda una copia fija del listado detectado, sin afectar sesiones previas.
- Solo Alimentos requiere caducidad; todos los módulos diarios exportan exclusivamente PDF.
- Si no cargaste el Excel, las listas de respaldo anteriores permanecen disponibles para Alimentos/Leches, y Vasos pide que se cargue un Excel.
- La corrección manual de una categoría se aplica a los conteos futuros, no mueve registros de una sesión ya abierta.
- Precaución: la clasificación propuesta debe revisarse antes de uso operativo, sobre todo los artículos bajo Revisar.

Para GitHub Pages: reemplaza `index.html`, publica y recarga con Ctrl+Shift+R.
