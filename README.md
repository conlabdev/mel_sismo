# Pulso territorial del Eje Cafetero

Tablero público y autocontenido para seguir el impacto y la recuperación de Manizales, Pereira y Santa Rosa de Cabal después del sismo del 10 de agosto de 2026, a partir de señales de conversación digital, dinámicas turísticas y arriendos.

## Contenido de la carpeta

- `index.html`: tablero completo, con datos, tipografías, identidad visual y funcionamiento incorporados.
- `README.md`: documentación de uso, alcance y actualización.

No se requieren librerías, servidor, instalación ni conexión a internet para consultar el tablero. Basta con abrir `index.html` en un navegador moderno.

## Qué muestra

El tablero organiza la lectura en cinco bloques:

1. **Contexto territorial:** presenta las tres ciudades con la misma jerarquía y sitúa el 10 de agosto de 2026 como referencia narrativa.
2. **Conversación y seguimiento post-sismo:** conserva el pulso trimestral por ciudad y añade una vista semanal de la atención en prensa. Esta segunda vista presenta la curva de ocho temas, una matriz de incidencia por cada 100 noticias y un ecualizador con los principales subtemas de cada semana.
3. **Indicadores comparables:** contrasta interés de búsqueda, presencia en medios y balance de sentimiento entre ciudades y periodos. Las definiciones están disponibles al pasar el cursor o enfocar los títulos.
4. **Arriendos — línea base:** presenta a las tres ciudades al mismo nivel. Manizales y Pereira usan el scraping del 22 de agosto de 2026; Santa Rosa de Cabal usa promedios de oferta por uso de la base territorial. Las fuentes y estadísticas no son directamente comparables.
5. **Explorador:** permite filtrar por ciudad, categoría e indicador, revisar la serie trimestral completa y descargar la selección visible.

## Fuentes incorporadas

- `base_indicadores_trimestral.csv`: 393 registros, 24 indicadores y cobertura entre 2019-T1 y 2026-T3.
- `base_cualitativa_trimestral.csv`: 470 registros sobre conversación en medios y búsquedas relacionadas en aumento.
- `arriendos_manizales_pereira.xlsx`: agregados públicos de 5.236 anuncios activos y no duplicados, tomados como línea base del 22 de agosto de 2026.
- `resumen_semanal_ancho.csv`: 1.228 noticias útiles organizadas en tres semanas ancladas al sismo, con conteos multietiqueta de grandes temas.
- `sismo_social_clasificado.csv`: clasificación determinista de subtemas mediante un diccionario auditable; el tablero incorpora únicamente agregados y no publica títulos, textos ni enlaces del corpus.

Los datos están incrustados dentro de `index.html`; los archivos fuente no deben copiarse a esta carpeta para que el tablero funcione.

## Alcance y precauciones

- El tablero es público y solo presenta resultados agregados.
- No incluye direcciones exactas, datos de anunciantes, enlaces de anuncios ni coordenadas.
- La oferta publicada en portales no equivale al inventario total de vivienda disponible.
- Las diferencias entre ciudades pueden reflejar composición por tipo de inmueble, cobertura del portal y presencia de fechas de publicación faltantes.
- Santa Rosa de Cabal conserva sus indicadores territoriales propios; no se le atribuyen cifras del archivo de arriendos, que solo cubre Manizales y Pereira.
- La fecha del sismo funciona como referencia temporal. Sin una medición anterior comparable no deben formularse conclusiones causales.
- El seguimiento semanal mide presencia dentro del corpus de prensa, no alcance, audiencia, opinión pública ni conversación ciudadana. El campo de interacción está vacío.
- Una noticia puede pertenecer a varios temas o subtemas; por ello, las incidencias temáticas pueden sumar más de 100.
- La semana 3 es un corte parcial con información disponible hasta el 26 de agosto, aunque su intervalo formal termina el día 30.
- El 80% del corpus proviene de Google News y el 27,9% de las noticias no recibió subtema. Estas condiciones deben considerarse al interpretar la agenda.
- La lectura semanal es regional: el 37,2% de las noticias no tiene ciudad identificada y el corpus no ofrece cobertura específica de Santa Rosa de Cabal suficiente para una comparación municipal.

## Publicación en GitHub Pages

1. Copiar únicamente `index.html` y `README.md` a la raíz del repositorio o a la carpeta que se publicará.
2. En GitHub, abrir **Settings → Pages**.
3. Elegir la rama y la carpeta de publicación.
4. Guardar la configuración.

GitHub Pages reconocerá `index.html` como página de inicio. Al ser autocontenido, no necesita proceso de compilación ni archivos adicionales.

## Actualización

Para conservar la trazabilidad, los nuevos cortes deben reemplazar los datos incrustados a partir de fuentes verificadas y mantener:

- la misma definición y unidad de cada indicador;
- la identificación explícita del periodo y municipio;
- la separación entre observaciones comparables y líneas de base;
- la exclusión de datos personales o de localización exacta;
- una revisión final de conteos, series, filtros y descargas.

**Última preparación:** 27 de agosto de 2026.
