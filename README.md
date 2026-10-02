# NucleIA

Aplicación web de un solo fichero para **contar núcleos en imágenes de microscopía de fluorescencia**, una a una o en lote. La imagen se procesa en el navegador y no se envía a ningún servidor.

**Usar la app:** https://fborrasumh.github.io/nucleia/

## Qué hace

- **Detección determinista:** elige el canal que define los núcleos (azul, verde, rojo, máximo o luminancia), resta el fondo irregular, aplica un umbral de Otsu con desplazamiento, limpia el ruido con una apertura morfológica y separa los núcleos que se tocan con transformada de distancia y *watershed* por semillas. Con la misma imagen y los mismos parámetros, siempre el mismo resultado.
- **Calidad por núcleo:** cada objeto se puntúa (tamaño relativo, circularidad, brillo, separación y contraste) y se clasifica como bueno, dudoso o para revisar.
- **Revisión manual:** se pueden quitar falsos positivos y añadir núcleos que falten; las correcciones se guardan por coordenadas y se reaplican si cambian los parámetros.
- **Marcadores:** positividad R, G y B por núcleo con umbrales automáticos (Otsu sobre las medias) o manuales, y combinaciones de perfiles.
- **Lote de imágenes:** se pueden abrir varias imágenes a la vez y analizarlas todas con los mismos parámetros, cada una con sus propias correcciones. Resumen comparativo con exportación a CSV y JSON; si cambian los parámetros, las demás imágenes se marcan como desactualizadas.
- **Escala:** con las micras por píxel, áreas en µm² y densidad en núcleos/mm².
- **Exportación:** JSON con los parámetros exactos, las correcciones y todas las medidas (para repetir el análisis), CSV y PNG con contornos.
- **Asistente opcional (OpenAI):** recibe solo un resumen en JSON, nunca la imagen, y se puede ver qué se enviaría antes de cada consulta. Sugiere ajustes y redacta métodos y resultados; no cuenta núcleos.

## Privacidad

Las imágenes y los recuentos no salen del navegador. Solo si se usa el asistente se envía un resumen JSON (parámetros y estadísticas) a OpenAI con la clave de quien lo usa.

## Límites

- El recuento depende de la calidad de la imagen y de los parámetros: debe revisarse siempre sobre la imagen antes de usarlo en un resultado. Núcleos muy apilados, fuera de foco o con fondo muy irregular pueden contarse mal.
- Se admiten PNG, JPG y WebP en color. Los TIFF solo los abre Safari: en otros navegadores hay que exportarlos antes a PNG.
- Las calidades y los umbrales de marcadores son guías para decidir qué revisar, no una validación.

## Autoría

Idea original de **Augusto Escalante Rodríguez** (Instituto de Neurociencias, CSIC–Universidad Miguel Hernández). Desarrollo conjunto con **Fernando Borrás Rocher** (Universidad Miguel Hernández de Elche).

## Cómo citar

Escalante Rodríguez, A. y Borrás Rocher, F. (2026). *NucleIA* (v1.0.0) [Software]. (DOI en trámite)

## Licencia

MIT. Véase [LICENSE](LICENSE).
