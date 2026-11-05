# ConteoVerde V10 — Dictado natural de 3 palabras + cronómetro

Aplicación web de inventario preparada para **GitHub Pages**. Su código principal está integrado en un solo `index.html` y no necesita instalar servidores. Mantiene el buscador SAP/SKU POS, las unidades, suma/resta, pick pack, carga de Merch y la opción **Sumar Conteos** de V9.

## Novedades de la V10

### 1. Voz natural y animada (sin selector)

Eliminamos **Estilo de voz**. En **Finalizar inventario → Dictado → Iniciar dictado**, la aplicación escoge automáticamente una voz en español disponible, dando preferencia a voces naturales y a español de México. Usa una entonación algo más ligera; el resultado real depende del navegador y las voces instaladas. **No es una voz grabada ni una imitación exacta de Jarvis**.

El dictado dice «SAP», guarda **1.15 segundos de silencio** y entonces lee los dígitos uno a uno. A continuación pronuncia **tres palabras consecutivas** extraídas del nombre real del artículo, seguidas de sus piezas y, cuando proceda, sus kilogramos o litros. Ejemplo: `CAKE POP VAINILLA`. **No concatena palabras alejadas del nombre**. Si el producto contiene menos de tres palabras, lee las que realmente tiene. Sigue disponible el selector de velocidad, así como pausa, anterior y siguiente.

### 2. Cronómetro discreto de inventario

Aparece en la zona superior del inventario, junto a «Finalizar inventario»:

- Comienza **con el primer movimiento válido** de suma o resta, no simplemente al cargar el Excel.
- Muestra el tiempo en formato **horas:minutos:segundos** (`00:00:00`).
- El botón **Ⅱ** permite pausarlo durante descansos y **▶** reanudarlo. Al registrar una nueva cantidad, el reloj vuelve a correr si estaba pausado.
- Se guarda en el almacenamiento del mismo navegador y conserva el transcurso al recargar; si sigue activo y dejas el navegador cerrado, el tiempo seguirá contando hasta que lo pauses o finalices. Para excluir descansos o interrupciones, **pausa el reloj antes de salir**.
- Al finalizar correctamente un reporte, el tiempo se congela. Si reabres ese inventario para editarlo, se reanuda sin perder el tiempo anterior.
- Se reinicia al importar otro inventario, reiniciar todos los conteos o confirmar una nueva lista Merch que reinicia el conteo.
- En inventarios de versiones anteriores, sin cronómetro guardado, el tiempo se **estima** desde el primer movimiento de su historial; puede incluir interrupciones previas.

### 3. Tiempo visible en resúmenes y reportes

- La ventana «Finalizar inventario» incluye **Tiempo total de conteo**.
- El reporte **Excel (.xlsx)** lo muestra en la fila 3, antes de la tabla de productos.
- El reporte **PDF** lo muestra en la franja verde del encabezado, en todas sus páginas.
- La vista **Dictado** muestra el mismo PDF, con el tiempo incluido.
- Al usar **Sumar Conteos**, si todos los participantes entregaron archivos con tiempo registrado, se muestra y exporta **Tiempo sumado de participantes**. Es la suma de las horas de trabajo individuales y **no equivale al tiempo total transcurrido si trabajaron simultáneamente**.
- Los archivos V9 (que todavía no incluían el tiempo) **se siguen pudiendo sumar**. Si falta el tiempo en alguno, el consolidado informa «No disponible» en vez de publicar un total engañoso.

## Uso básico

1. Abre ConteoVerde y carga un inventario `.xls` o `.xlsx`.
2. Busca por descripción o SAP; si cargaste previamente la lista Merch, también por SKU POS.
3. Selecciona la unidad (piezas por defecto), suma o resta cantidades y usa el botón de caja/pick pack cuando exista.
4. El reloj comienza al primer movimiento. Páusalo si interrumpes el trabajo.
5. Selecciona **Finalizar inventario** y elige Excel, PDF, Dictado o Sumar Conteos.
6. Si trabajaron varias personas, cada una exporta su XLSX y luego unifican los reportes desde **Σ Sumar Conteos**.

## Publicar / actualizar en GitHub Pages

1. Descarga el paquete ZIP de V10 y descomprímelo.
2. Sustituye `index.html` del repositorio que usas actualmente; conserva `.nojekyll` y la licencia si ya estaban.
3. Publica el cambio en la rama configurada de GitHub Pages.
4. Actualiza el navegador con **Ctrl + Shift + R**. Confirma que se muestra `V10 · TIEMPO + DICTADO NATURAL`.

Los catálogos y conteos se guardan en el dispositivo local. La lista Merch **no se incluye precargada** en el ZIP: cárgala en cada navegador con el botón **Actualizar lista Merch**. Los sitios públicos de GitHub Pages no ofrecen privacidad para los datos incorporados directamente al HTML.

## Compatibilidad y verificaciones

Se probó la carga del reporte antiguo `.xls` de 285 productos, la lectura del inventario anterior, la pausa/reanudación del cronómetro, la visualización de las tres palabras consecutivas, la síntesis de voz en navegador simulado, los XLSX exportados y leídos nuevamente, los PDF y la consolidación con y sin tiempos disponibles.

La calidad final de la voz y la apertura en una instalación específica de Microsoft Excel dependen del equipo del usuario; se recomienda probarlos en el navegador y computadora donde se realizará el inventario.
