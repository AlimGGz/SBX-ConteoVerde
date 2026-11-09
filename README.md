# ConteoVerde V15 — Dictado especial para Material LSM normal

Esta versión incorpora una excepción **solo en el dictado** para los productos cuya familia en el Excel sea `Material LSM normal`. No modifica el SAP, las descripciones originales, los totales, los reportes ni los conteos existentes.

## Ajuste realizado

- Para **Material LSM normal**, se buscan **tres palabras consecutivas** de la descripción que contengan únicamente letras. Se aceptan abreviaturas como `PLSTC`, `CLDCP`, `GID`, `SS`, `TMBLR` y `THRLD`, que antes eran descartadas.
- Se excluyen los fragmentos con números (por ejemplo, `SM26`, `C2P`, `24OZ`, `CJ24PZAS`) y los números escritos como palabras (por ejemplo, «DOS»).
- Se prioriza una secuencia de tres palabras **realmente adyacentes** en el nombre original. Si las cifras interrumpen la secuencia, se ignoran los fragmentos numéricos y se eligen palabras alfabéticas consecutivas de la lista limpia.
- Cuando hay varias ternas válidas, el programa elige una de forma variada pero **estable para el mismo SAP** (no cambia inesperadamente al repetir un artículo).
- Si el nombre original solo contiene **una o dos palabras alfabéticas**, se dictan esas palabras. No se inventa una tercera ni se añade un número para completar tres.
- Para **todas las demás familias**, continúa funcionando exactamente el filtro estricto de V14: sin números, códigos ni presentaciones de Pick Pack en las palabras clave.

## Ejemplos de Material LSM normal

| Producto en Excel | Ejemplo de palabras pronunciadas |
| --- | --- |
| `78934 C2P SM26 PLSTC CLDCP GID 24OZ` | `PLSTC CLDCP GID` |
| `78973 C2P SM26 SS TMBLR DRNK THRLD 16OZ` | Tres palabras consecutivas del tramo `SS TMBLR DRNK THRLD` |
| `79003 C2P SM26 PLSTC CLDCP 24OZ` | `PLSTC CLDCP` (solo tiene dos palabras sin cifras) |

**Advertencia:** «palabras» se entiende como fragmentos alfabéticos del nombre original. Las abreviaturas técnicas pueden sonar letra por letra o con la pronunciación disponible en el navegador. Los archivos XLSX y PDF **no se modifican**.

## Actualizar GitHub Pages

1. Descarga el ZIP y extrae su `index.html`.
2. Reemplaza el archivo `index.html` existente en tu repositorio, sin modificar el catálogo de inventario.
3. Publica el cambio y recarga la aplicación con **Ctrl + Shift + R**.
4. Comprueba la etiqueta `V15 · LSM SIN NÚMEROS`.
5. En un conteo de prueba, selecciona un producto de **Material LSM normal** y ve a **Finalizar inventario → Dictado**.

El cambio no reinicia los conteos ni afecta la lista Merch. Se mantienen la pausa tras decir «SAP», la pausa entre piezas y KG/L, la espera de 1 a 5 segundos entre artículos, y la consolidación de reportes.
