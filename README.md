# ConteoVerde V14 — Dictado más claro

Esta versión se basa en ConteoVerde V13 y **mantiene** la importación de inventarios `.xls`/`.xlsx`, el catálogo auxiliar Merch, la búsqueda SAP y SKU POS, los botones de suma, resta y Pick Pack, el cronómetro, la generación de PDF/Excel y **Sumar Conteos**.

## Cambios en el dictado

### 1. Palabras clave sin códigos, números ni presentaciones

La aplicación busca **hasta tres palabras consecutivas** en la descripción original del artículo. Descarta cualquier bloque que incluya una cifra o un término utilizado para códigos, unidades de peso, capacidad, cajas, paquetes y Pick Pack.

Ejemplos:

| Descripción original | Palabras clave que se leen |
| --- | --- |
| `CAKE POP VAINILLA CJ12BLISTER3PZAS1.66KG` | `CAKE POP VAINILLA` |
| `CJ24PZAS110GR GALLETAS DE AVENA 24G` | `GALLETAS DE AVENA` |
| `COLD BREW CONCENTRADO 1L CJ6PZAS` | `COLD BREW CONCENTRADO` |
| `CJ1500` | `Descripción no identificable` |

**Importante:** si hay menos de tres palabras consecutivas válidas, se pronuncian solo las disponibles. Nunca se juntan palabras distantes saltando códigos para alcanzar tres artificialmente. El SAP se sigue dictando **por separado**, dígito por dígito.

### 2. Pausa independiente entre piezas y KG/L

Cuando un artículo tiene una cantidad contabilizada en kilogramos o litros, el dictado sigue este flujo:

1. Dice «SAP».
2. Espera **1.15 segundos**.
3. Dice los dígitos, las palabras clave y la cantidad en piezas.
4. Espera **1.25 segundos**.
5. Dice la cantidad en kilogramos o litros.
6. Espera el intervalo configurable de **1 a 5 segundos** antes del siguiente artículo.

Las esperas comienzan cuando termina la voz anterior (no se simulan solo con puntuación). Si se pulsa **Pausar**, se conserva el tiempo pendiente y se reanuda después.

### 3. Pronunciación mejorada de anglicismos

Los nombres del Excel, PDF y pantalla **no se modifican**. Solo al hablar se aplican pronunciaciones adaptadas al español para anglicismos frecuentes, por ejemplo:

- `CAKE POP` → «quéik pop».
- `COOKIE` → «cúqui».
- `COLD BREW` → «cóuld brú».
- `BROWNIE` → «bráuni».
- `TUMBLER` → «támbler».
- `SNOOPY` → «snúpi».

La claridad final depende de las voces de síntesis que ofrezcan Windows, Chrome, Edge o el dispositivo. No es una grabación de voz preinstalada ni un servicio externo.

## Instalar la actualización en GitHub Pages

1. Descarga el ZIP de la V14.
2. Extrae `index.html` y reemplaza el archivo del mismo nombre en tu repositorio.
3. Confirma los cambios en la rama utilizada por GitHub Pages.
4. Actualiza la página con **Ctrl + Shift + R**.
5. Comprueba que diga `V14 · DICTADO MÁS CLARO`.
6. Carga tu Excel, realiza un conteo de prueba y elige **Finalizar inventario → Dictado**.

No es necesario actualizar la lista Merch ni reiniciar el inventario por el simple hecho de reemplazar `index.html`. Antes de comenzar cualquier prueba en un inventario real, guarda una copia del reporte.

## Verificaciones realizadas

- Importación del Excel proporcionado con **285 SAP únicos**.
- Selección de palabras clave contra las **285 descripciones**: sin cifras, gramajes, códigos SAP/SKU ni términos de Pick Pack en las frases seleccionadas.
- Prueba temporal de voz simulada verificando **1.15 s tras SAP** y **1.25 s antes de KG/L**.
- Verificación de que la pausa conserva el tiempo pendiente y que el siguiente producto respeta la configuración de **1 s**.
- Validación de sintaxis de los siete scripts integrados y ausencia de errores de JavaScript durante las pruebas del dictado.

La pronunciación audible exacta no puede garantizarse en todos los navegadores; recomendamos probarla en Chrome o Edge en el equipo donde se use.
