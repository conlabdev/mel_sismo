# Pulso social del Eje Cafetero

**[Abrir el visor](05_entregas/visor_pulso.html)**. Funciona sin conexión. El corredor está formado por **Manizales, Chinchiná, Santa Rosa de Cabal, Pereira, Dosquebradas y Armenia**.

## Qué consultar

1. **Sismo**: volumen semanal, clasificación de relación con el 10 de agosto de 2026 y temas. El botón de noticias abre titulares, medios, fechas y enlaces; permite descargar referencias.
2. **Arriendos**: mediana del canon, variación de la mediana entre cortes de la misma serie, proporción de anuncios publicados antes/después/sin fecha y evolución. La muestra es un dato secundario.
3. **Series históricas**: Google Trends, volumen de prensa y balance de sentimiento. Todas las gráficas tienen último mes, tres meses, último año, serie completa y fechas personalizadas. Las fechas de las series semanales corresponden al inicio de la semana.
4. **Fuentes y cobertura**: detalle del corredor y de los portales, dentro de un botón. No ocupa la vista principal.

## Estado de las fuentes

El corte vigente es el que se documenta inmediatamente abajo. No son publicaciones verificadas de Facebook, Instagram o X. Las historias municipales tienen distintas coberturas y no deben compararse como censos.

### Corte extraordinario · 7 de septiembre de 2026, 13:49 (Colombia)

La actualización semanal incorporó prensa entre el 24 de agosto y el 7 de septiembre, con solapamiento para deduplicar. El corpus queda en 17.431 noticias únicas; 14.906 tienen al menos un municipio del corredor. Google News produjo ventanas subdivididas o saturadas, por lo que su cobertura es observada y no exhaustiva. Los ocho RSS directos respondieron correctamente. GDELT devolvió HTTP 429 en las seis consultas; se conserva su histórico y el fallo queda visible en la cobertura, sin reemplazarlo por ceros.

Fincaraíz se capturó el 7 de septiembre para los seis municipios y mantiene la serie separada del histórico multiportal. Las diferencias entre el total declarado por el portal y los avisos recuperados aparecen como `parcial_o_diferencia`; no se presentan como cobertura completa. El sentimiento clasificó de manera incremental 104 noticias nuevas o modificadas con el modelo local Robertuito y conserva el caché anterior.

Google Trends quedó actualizado el 7 de septiembre para Chinchiná, Dosquebradas, Santa Rosa de Cabal, Pereira y Armenia, con 261 semanas cerradas por ciudad. La consulta de Manizales fue limitada por Google; el visor conserva su última serie válida y el manifiesto registra el fallo. No se incluyen semanas parciales como semanas cerradas.

La auditoría final pasó a las 13:49: los seis municipios están presentes, el total regional se calcula como unión de noticias y las entregas no contienen direcciones, anunciantes, coordenadas, URL ni texto de anuncios. La semana iniciada el 7 de septiembre se identifica como parcial en la base y en el visor. Esta conversación y su actualización semanal usan **GPT-5.6 Terra**; la programación se ejecuta los lunes a las 9:00 a. m., hora de Colombia.

El histórico multiportal conserva cortes de 22 de agosto y 2 de septiembre de 2026. La captura Fincaraíz de 6 de septiembre contiene 1.945 anuncios de los seis municipios y es una serie separada. No comparar una mediana multiportal con una de un único portal como si hubiera cambiado el mismo mercado observado. La variación histórica original entre anuncios repetidos se conserva en la tabla de detalle, diferenciada de la variación entre medianas de stock.

Google Trends conserva una extracción completa por municipio y descarta la semana en curso. Para Chinchiná, una consulta HTTP previa devolvió 429, pero la interfaz oficial permitió documentar la tabla completa. `actualizar_tendencias.py` guarda respuestas y manifiestos, conserva la serie previa ante un fallo y evita empalmar escalas normalizadas. Cada índice se normaliza dentro de su propia consulta: no comparar niveles entre municipios como volúmenes absolutos.

El sentimiento se clasifica sobre el corpus propio de los seis municipios. El entorno de inferencia está instalado en `03_rutinas/.venv`, con el modelo Robertuito local y la revisión fijada en la rutina. Reutiliza textos idénticos y procesa sólo los nuevos o modificados; no necesita leer el OAT ni descargar el modelo al actualizar.

RSS directos conserva ocho medios. La última captura GDELT falló; se preserva el histórico y el manifiesto de errores. Google News tiene ventanas saturadas, visibles en cobertura. La fecha GDELT es primera detección y no necesariamente publicación.

## Método de relación con el sismo

`analisis_pulso.py` vuelve a clasificar el corpus de forma reproducible. **Explícita** exige texto sísmico, mención al 10 de agosto, municipio del corredor y fecha desde el evento. **Probable** exige texto sísmico y contexto municipal desde el evento; necesita revisión contextual. **Dudosa** comprende reconstrucción, ayudas o vivienda sin vínculo sísmico suficiente y queda fuera del volumen principal. Se excluyen referencias inequívocas a varios eventos extranjeros y se admite corrección manual por ID. No se infiere causalidad.

El total regional es la unión de noticias. Los temas son multietiqueta y no suman necesariamente el volumen total. La vista estricta permite analizar sólo las referencias explícitas al evento.

## Dónde está cada cosa

| Carpeta | Contenido y uso |
|---|---|
| `01_documentacion` | Fichas de fuente, catálogo, inventario de rutinas y controles internos. No son entregables para compartir. |
| `02_datos` | Originales por fuente, capturas fechadas y tablas de trabajo. `indicadores` conserva la numeración que conecta cada fuente con su rutina. |
| `03_rutinas` | Programas propios de este proyecto. `Actualizar.ps1` es la entrada. `_dependencias` contiene las bibliotecas necesarias; no se ordena manualmente. |
| `04_visor` | Una única plantilla, estilos e interacciones. Cambiar aquí el diseño y reconstruir; no editar el HTML final. |
| `05_entregas` | Resultados vigentes para abrir, descargar o compartir. No crear variantes `final_v2`. |

Este README reúne la guía humana y el protocolo operativo. Las fichas técnicas se conservan como documentación de las fuentes, no como instrucciones alternativas de actualización. Los README dentro de bibliotecas o modelos pertenecen a esos componentes y conservan información de uso/licencia.

El proyecto es autónomo: no lee ni escribe el otro proyecto ni utiliza la antigua carpeta `oat/data`. Las copias iniciales de los insumos evolucionan por separado. No crear enlaces entre proyectos.

## Cómo ejecutar

Desde esta carpeta, con PowerShell:

```powershell
.\03_rutinas\Actualizar.ps1 -Modo Reconstruir
.\03_rutinas\Actualizar.ps1 -Modo Capturar -Desde AAAA-MM-DD -Hasta AAAA-MM-DD
```

`Reconstruir` usa únicamente los insumos locales. `Capturar` consulta las fuentes automáticas indicadas en el protocolo y después reconstruye. El lanzador busca primero `03_rutinas/.venv`, después el Python disponible en Codex y finalmente Python del sistema. Los requisitos particulares de cada fuente se conservan con su configuración; no reutilizar un entorno alojado en el otro proyecto.

Cada ejecución registra resultados por rutina y huellas de las entregas en `01_documentacion/actualizaciones`. Revisar el estado de cada fuente; una rutina opcional fallida puede conservar la última información válida. No afirmar que una fuente se actualizó porque el visor se reconstruyó.

## Protocolo semanal para un agente

Versión 3 · 7 de septiembre de 2026. Instrucciones suficientes para un agente que no conoce esta conversación.

## Alcance fijo

Pulso social de **Manizales, Chinchiná, Santa Rosa de Cabal, Pereira, Dosquebradas y Armenia**. No agregar departamentos como unidades. Caldas, Risaralda y Quindío sirven para desambiguar búsquedas. Monitorear la agenda regional general y distinguir menciones de sismo y posible seguimiento al evento del 10 de agosto de 2026. No atribuir causalidad por proximidad temporal.

## Secuencia de cada semana

1. Leer la sección de estado de este README, este protocolo y el último registro de `actualizaciones`. Identificar la última semana con cobertura. La semana va de lunes a domingo, hora de Colombia.
2. Elegir el rango desde el lunes de la semana anterior a la última semana completa hasta el domingo más reciente. Mantener al menos 14 días de solapamiento para recuperar publicaciones tardías. No reemplazar el histórico con el resultado de la nueva consulta.
3. Desde la raíz, ejecutar `03_rutinas/Actualizar.ps1 -Modo Capturar -Desde AAAA-MM-DD -Hasta AAAA-MM-DD`. La captura de arriendos usa la fecha real del día de descarga, aunque el rango de prensa sea histórico.
4. Revisar `01_documentacion/control/cobertura_corredor.csv`, `01_documentacion/control/cobertura_fuentes_prensa.csv` y `02_datos/procesados/arriendos_fincaraiz.csv`. Un proceso terminado no garantiza cobertura completa. Identificar fuentes fallidas, ventanas saturadas y exclusiones por municipio.
5. Revisar una muestra de títulos de cada municipio en el corpus de trabajo, especialmente Armenia y Pereira por ambigüedad; revisar menciones de sismo y de reconstrucción. Registrar las decisiones de revisión en `02_datos/social/revision_evento.csv`: columnas `id,relacion_evento,motivo,revisor,fecha_revision`. Las clases admitidas son `explicita_10_agosto`, `seguimiento_probable`, `dudosa`, `actualidad_general`. El ID se obtiene de la descarga de referencias del visor. Conservar motivo y autor; las reglas temáticas del evento están en `03_rutinas/analisis_pulso.py`.
6. Ejecutar `-Modo Reconstruir` después de ajustes. Verificar auditoría correcta, filtros del visor, semana seleccionada, tabla de fuentes y ambas series de arriendos.
7. Actualizar la sección de estado de este README con fecha real de cada fuente, nuevos datos, fallos, cobertura y próxima acción. No afirmar que se actualizaron redes sociales si solo se recuperó prensa. No publicar automáticamente en internet.

## Qué hace cada captura

- **Google News**: búsquedas generales para las seis ciudades. Divide ventanas hasta un día si llega a 100 resultados. Si un día alcanza el límite, conserva `saturada`; no se declara exhaustivo. Guarda XML, consulta, fechas, estado y registros.
- **RSS directos**: lee los ocho medios configurados en `03_rutinas/social/config.py`. Los feeds son recientes y pueden no recuperar toda la semana anterior. Guarda respuesta y errores; el ámbito departamental del medio no determina por sí solo el municipio de la noticia.
- **GDELT**: consultas por municipio, divisiones por saturación, separación de seis segundos y registro de fallos. `seendate` es fecha de detección, no necesariamente publicación. La entrega identifica este límite. Si falla, conservar los datos antiguos y reportar el faltante; nunca introducir cero ni borrar la lista de fallos.
- **Fincaraíz**: recorre los cinco tipos residenciales de cada municipio y todas las páginas declaradas; excluye avisos cuya ciudad estructurada no coincide. Conservar los originales, los excluidos por geografía y la diferencia frente al total publicado. Esta serie corresponde a un solo portal.
- **Redes sociales**: no hay una fuente de publicaciones verificada en el corpus inicial. Los conectores heredados son experimentales; no se ejecutan como parte del proceso certificado. Para incorporarlos se requiere validar acceso, fecha, municipio y esquema primero.

## Reglas de agregación

La URL y la combinación conservadora de título, medio y fecha eliminan duplicados. Los municipios se detectan en el texto. Noticias sin municipio quedan en el corpus interno, fuera de los totales del corredor. La misma noticia puede entrar en dos municipios; el total regional se calcula como unión. No sumar las ciudades para obtenerlo.

La fecha sin hora conserva su día original. Fechas con zona horaria se convierten a Colombia. En GDELT se identifica la fecha de detección. Los temas usan un diccionario multietiqueta y no representan diagnósticos de daños. Un mes o una semana sin registros no se rellena con cero.

## Histórico multiportal de arriendos

El Excel original conserva cortes del 22 de agosto y 2 de septiembre. Manizales y Pereira tienen dos cortes; Armenia y Santa Rosa solo una línea de base. Las nuevas capturas Fincaraíz permanecen separadas de ese universo.

Para ampliar el histórico multiportal, capturar nuevamente Fincaraíz, Ciencuadras y Metrocuadrado con cobertura registrada por municipio/tipo. El esquema de entrada `corte_PORTAL.json` y el normalizador están en `03_rutinas/arriendos/construir_corte.py`. Ejecutar su `--help`; usar `--entrada`, `--excel` y `--fecha` explícitos. Trabajar primero sobre una copia fechada del Excel dentro de `02_datos/arriendos`, verificar con `test_logica.py` y `resumen_corte.py`, y reemplazar el vigente solo tras conciliar hojas, cortes, anuncios y cobertura.

No ejecutar recetas antiguas que interceptan credenciales o dependen de `/mnt`. El runbook original queda como referencia de campos y reglas; la captura HTTP de Fincaraíz y este protocolo son las instrucciones vigentes. Ante bloqueo de acceso, registrar la fuente pendiente, sin inferir ausencia de oferta.

## Criterios de cierre

Auditoría con estado correcto; seis municipios presentes en cobertura; total semanal conciliado con la unión de noticias; fecha del visor coherente; fuentes fallidas visibles; ninguna dirección, anunciante, coordenada o enlace individual de arriendo en las entregas; ninguna lectura del observatorio turístico. Dejar la próxima acción concreta en la sección de estado de este README.

## Series y actualizaciones adicionales

La reconstrucción ejecuta `actualizar_semanal.py`, el ensamble de Fincaraíz, `analisis_pulso.py`, la auditoría y el generador del visor. La captura semanal añade Google News, RSS/GDELT, Fincaraíz y `actualizar_tendencias.py`. Un límite temporal de Google se registra como fallo y no borra series antiguas. No insistir con proxies, cuentas alternativas o evasión de límites.

Para reintentar sólo una serie:

```powershell
python .\03_rutinas\actualizar_tendencias.py --municipios "Chinchiná"
.\03_rutinas\Actualizar.ps1 -Modo Reconstruir
```

Usar el mismo intérprete que el lanzador. Los puntos de Google Trends quedan en `02_datos/tendencias`; la copia inicial de las cuatro series está en `02_datos/indicadores/01_rs_5_indice_busquedas_google`. El ensamble prioriza la extracción propia más reciente para cada municipio.

El sentimiento ya cubre los seis municipios y usa exclusivamente el corpus propio. `actualizar_sentimiento.py` reutiliza las clasificaciones de textos idénticos y procesa los nuevos o modificados con el modelo local. El entorno de inferencia está instalado en `03_rutinas/.venv`. Registrar modelo, revisión y fecha; si falla la inferencia, conservar el caché anterior e informar su cobertura real. No copiar resultados futuros del OAT ni atribuir a una ciudad clasificaciones de otra.

El JSON de trabajo del visor está en `02_datos/procesados/analisis_visor.json`. Los originales inmobiliarios con direcciones y anunciantes permanecen internos; el visor sólo contiene agregados de arriendos.

## Entregas vigentes

En `05_entregas` quedan únicamente el visor, `pulso_semanal.csv` (contexto regional y relación con el sismo) y `arriendos_seguimiento.csv` (ambas series, medianas, fechas de publicación y porcentajes). La cobertura por fuente queda en `01_documentacion/control`; los detalles de trabajo, en `02_datos/procesados`.

La reconstrucción, las capturas básicas y la clasificación incremental de sentimiento funcionan con el entorno propio actual. La cobertura de sentimiento de los seis municipios fue conciliada con los IDs del corpus el 7 de septiembre de 2026.

## Verificación del cierre

La reconstrucción se probó bloqueando la red y cualquier lectura del otro proyecto. Las fuentes protegidas se contrastaron con sus huellas antes de borrar las carpetas antiguas. `oat/data` y `_archivo_oat_20260906` fueron eliminadas. La preparación temporal del entorno de inferencia también se eliminó; sólo queda el entorno útil dentro de este proyecto.

Para comprobar o continuar el sentimiento sin descargar prensa:

```powershell
.\03_rutinas\.venv\Scripts\python.exe .\03_rutinas\actualizar_sentimiento.py
.\03_rutinas\Actualizar.ps1 -Modo Reconstruir
```

El caché de clasificación conserva ID, hash del texto, etiqueta, confianza, modelo, revisión y fecha. Un cambio de texto obliga a reclasificar. Las capturas semanales ejecutan esta misma rutina después de construir el corpus propio.


### Alternativa de Google Trends mediante su interfaz

Si la captura HTTP está limitada y la página oficial funciona, abrir Google Trends con el nombre exacto del municipio, Colombia, últimos cinco años, búsqueda web y todas las categorías. Conservar la tabla completa de interés a lo largo del tiempo, sus fechas y valores en un JSON dentro de `02_datos/tendencias/capturas/<fecha>_<municipio>/tabla_google.json`, siguiendo el ejemplo de Chinchiná del 7 de septiembre. Comprobar continuidad semanal; guardar URL, fecha de consulta y método. No cambiar de red ni evadir controles de acceso. Importar con el intérprete del proyecto:

```powershell
.\03_rutinas\.venv\Scripts\python.exe .\03_rutinas\importar_tendencias_interfaz.py .\02_datos\tendencias\capturas\20260907T110000_interfaz_chinchina\tabla_google.json
.\03_rutinas\Actualizar.ps1 -Modo Reconstruir
```

El importador valida el corredor, el rango 0–100 y la consulta, conserva el original, excluye las semanas no cerradas y actualiza el manifiesto. La captura fallida previa permanece como registro del intento; el manifiesto correcto de la interfaz documenta la recuperación. Si tampoco funciona la interfaz, conservar la serie anterior y registrar la fuente pendiente.


Las gráficas temporales de Pulso señalan el sismo del 10 de agosto de 2026 con una línea naranja y fondos suaves a cada lado. En «Serie completa», las series que comienzan después del evento incluyen su fecha como referencia, conservando vacío el tramo sin observaciones. Si un rango elegido excluye el evento, una nota indica si queda antes o después.


## Actualización programada en la aplicación

Conversación: **Pulso · actualización semanal**. Los lunes a las 9:00 a. m., hora de Colombia. Primera ejecución prevista: 14 de septiembre de 2026. Actualiza desde el último corte exitoso y consolida semanas completas.

La programación está activa y retoma la misma conversación, siguiendo este README. Requiere el computador encendido, la aplicación abierta y acceso a los archivos y fuentes. Si una fuente falla, conserva su último corte e informa el pendiente; no garantiza datos que la fuente no publique.

Identificadores para localizar o modificar la programación sin duplicarla: automatización `pulso-actualizaci-n-semanal`; conversación `01a07d19-8513-7d80-87f5-5ef296e39cad`. Los horarios se administran en la aplicación: editar este README por sí solo no cambia la programación.
