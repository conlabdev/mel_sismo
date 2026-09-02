# Pulso territorial del Eje Cafetero

Tablero público y autocontenido para seguir señales de impacto y recuperación en Manizales, Pereira, Santa Rosa de Cabal y Armenia después del sismo del 10 de agosto de 2026. Integra conversación digital, dinámicas turísticas y oferta de vivienda en arriendo.

## Contenido de la carpeta

- `index.html`: tablero completo, con datos, tipografías, identidad visual e interacciones incorporadas.
- `README.md`: documentación de uso, alcance y actualización.

No se requieren librerías, instalación, servidor ni conexión a internet. Basta con abrir `index.html` en un navegador moderno. La carpeta está lista para publicarse directamente con GitHub Pages.

## Qué muestra

El tablero organiza la lectura en cinco bloques:

1. **Contexto territorial:** presenta las cuatro ciudades con la misma jerarquía y sitúa el 10 de agosto de 2026 como referencia temporal.
2. **Conversación y seguimiento post-sismo:** combina el pulso trimestral por ciudad con una vista semanal de la atención en prensa. Incluye curva de temas, matriz de incidencia por cada 100 noticias y ecualizador de subtemas.
3. **Indicadores comparables:** contrasta interés de búsqueda, presencia en medios y balance de sentimiento entre las ciudades y periodos para los que existe información. Las definiciones y fuentes aparecen al pasar el cursor o enfocar los títulos.
4. **Arriendos:** usa una sola fuente y una metodología común para las cuatro ciudades. El corte del 2 de septiembre reúne 5.426 avisos activos y no duplicados. Manizales y Pereira ya permiten comparar con el 22 de agosto; Armenia y Santa Rosa de Cabal establecen su primera medición comparable.
5. **Explorador:** permite filtrar por ciudad, categoría e indicador, revisar la serie trimestral completa y descargar la selección visible.

## Fuentes incorporadas

- `base_indicadores_trimestral.csv`: 478 registros cuantitativos, 24 indicadores y cobertura entre 2019-T1 y 2026-T3.
- `base_cualitativa_trimestral.csv`: 630 registros de principales temas en medios y búsquedas relacionadas en aumento.
- `arriendos_manizales_pereira.xlsx`: corte del 2 de septiembre de 2026 con 6.545 observaciones capturadas y 5.426 avisos activos no duplicados en Manizales, Pereira, Santa Rosa de Cabal y Armenia. Las 48 combinaciones de ciudad, portal y tipo de vivienda emplean la misma metodología; 47 coincidieron exactamente con el total visible en el portal.
- `resumen_semanal_ancho.csv`: 1.228 noticias útiles organizadas en tres semanas ancladas al sismo, con conteos multietiqueta de grandes temas.
- `sismo_social_clasificado.csv`: clasificación determinista de subtemas mediante un diccionario auditable. El tablero incorpora solo agregados y no publica títulos, textos ni enlaces del corpus.

Los datos están incrustados dentro de `index.html`; los archivos fuente no deben copiarse a esta carpeta para que el tablero funcione.

## Cómo leer los cambios de arriendos

- **Manizales:** el stock observado pasó de 642 a 635 avisos. Se identificaron 158 ofertas nuevas reales y 178 salidas; la mediana del cambio de canon entre 464 avisos comparables fue 0%.
- **Pereira:** el stock observado pasó de 4.594 a 4.324 avisos. Se identificaron 158 ofertas nuevas reales y 436 salidas; la mediana del cambio de canon entre 4.158 avisos comparables fue 0%.
- **Armenia y Santa Rosa de Cabal:** el 2 de septiembre es la primera medición comparable. Sus entradas, salidas y variaciones de canon podrán calcularse en el siguiente corte.

El balance del stock no tiene que coincidir aritméticamente con nuevas ofertas menos salidas, porque la comparación controla cambios de cobertura y de identificación entre portales.

## Alcance y precauciones

- El tablero es público y solo presenta resultados agregados.
- No incluye direcciones exactas, datos de anunciantes, enlaces de anuncios ni coordenadas.
- La oferta publicada en portales no equivale al inventario total de vivienda disponible.
- Las diferencias entre ciudades pueden reflejar composición por tipo de inmueble, cobertura del portal y fechas de publicación faltantes.
- La fecha del sismo funciona como referencia temporal. La coincidencia temporal no demuestra causalidad.
- El seguimiento semanal mide presencia dentro del corpus de prensa, no alcance, audiencia, opinión pública ni conversación ciudadana. El campo de interacción está vacío.
- Una noticia puede pertenecer a varios temas o subtemas; por ello, las incidencias temáticas pueden sumar más de 100.
- La semana 3 es un corte parcial con información disponible hasta el 26 de agosto, aunque su intervalo formal termina el día 30.
- El 80% del corpus proviene de Google News y el 27,9% de las noticias no recibió subtema.
- La lectura semanal es regional: el 37,2% de las noticias no tiene ciudad identificada y el corpus no permite comparar de forma municipal a Santa Rosa de Cabal y Armenia.

## Publicación en GitHub Pages

1. Copiar únicamente `index.html` y `README.md` a la raíz del repositorio o a la carpeta que se publicará.
2. En GitHub, abrir **Settings → Pages**.
3. Elegir la rama y la carpeta de publicación.
4. Guardar la configuración.

GitHub Pages reconocerá `index.html` como página de inicio. Al ser autocontenido, no necesita compilación ni archivos adicionales.

## Actualización

Para conservar la trazabilidad, cada nuevo corte debe reemplazar los datos incrustados a partir de fuentes verificadas y mantener:

- la misma definición y unidad de cada indicador;
- la identificación explícita del periodo y municipio;
- la separación entre observaciones comparables y primeras líneas de base;
- la exclusión de datos personales o de localización exacta;
- una revisión final de conteos, series, filtros, descargas y copia publicada.

**Última preparación:** 2 de septiembre de 2026.
