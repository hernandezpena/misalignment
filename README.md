# Inventario de casos de desalineación en IA de frontera

Registro de casos documentados de desalineación (*misalignment*) en modelos de los principales laboratorios de IA.

**Consulta en línea:** https://hernandezpena.github.io/misalignment/

Observatorio de **PrivaIA Lab Navarra**, Facultad de Derecho y DATAI, Universidad de Navarra.

---

## Qué es

Un inventario abierto y en actualización continua de comportamientos en los que un sistema de IA de frontera actúa en contra de las intenciones de sus desarrolladores o usuarios. Cada caso incluye fecha, laboratorio y modelo implicados, fuente verificable, valoración de la gravedad, respuesta del laboratorio y relevancia en el marco jurídico de la Unión Europea (Reglamento de IA, DSA, RGPD, CEDH).

El observatorio tiene carácter jurídico, no periodístico: los contenidos son accesibles al público, con el registro y la solidez propios del trabajo académico.

## Contenido del repositorio

| Archivo | Función |
|---|---|
| `index.html` | Página web del inventario. No es necesario modificarla. |
| `incidentes.csv` | Datos del inventario de desalineación: una fila por caso. |
| `gobernanza.csv` | Inventario separado de fallos de gobernanza interna de los laboratorios (véase más abajo). |
| `README.md` | Este documento. |

La página lee `incidentes.csv` y genera automáticamente el cuadro resumen, los gráficos, el mapa de calor y las fichas de casos. La pestaña «Gobernanza» lee `gobernanza.csv` y muestra su cuadro resumen, la distribución por tipo y las fichas, con enlaces cruzados a los casos de desalineación.

## Criterios del inventario

**Definición.** Se entiende por desalineación que un sistema de IA persiga de forma sistemática un objetivo o una conducta distinta de la pretendida por quienes legítimamente lo dirigen, o contraria a los valores que declara el propio laboratorio.

**Exclusiones.** Se excluyen:

- el uso malicioso por terceros;
- los *jailbreaks*, salvo que el modelo inicie la elusión o haga por su cuenta algo de la tipología C1–C9;
- los errores factuales aislados y las alucinaciones, aunque tengan efectos jurídicos;
- las salidas aisladas sin indicio de conducta sistemática.

**Excepciones.** Se mantienen, marcados como controvertidos y con una nota que explica la excepción:

- los casos en que terceros indujeron la conducta, cuando son un precedente relevante de aprendizaje en despliegue sin salvaguardas (MA-01);
- las salidas aisladas que contradicen de forma grave los valores declarados del laboratorio, se dirigen contra la persona usuaria (hostilidad o incitación al daño) y el laboratorio reconoce como contrarias a sus políticas (MA-08).

**Fallos de gobernanza.** Cuando la conducta del sistema se explica por una decisión u omisión organizativa del desarrollador, y no porque el modelo persiga por su cuenta otra conducta, el caso se registra en el inventario de gobernanza (`gobernanza.csv`), no en este.

**Fuentes**, por orden de preferencia: documentación de los laboratorios (fichas técnicas, informes y artículos), evaluaciones de terceros independientes, resoluciones y procedimientos públicos, y periodismo de investigación. Los casos con hechos o causalidad en discusión se marcan como controvertidos.

**Estado de verificación**

| Valor | Criterio |
|---|---|
| Verificado | La fuente principal es primaria: documentación o informe del desarrollador, artículo científico, informe de un evaluador independiente o resolución judicial o administrativa. |
| En desarrollo (información periodística) | El caso solo está documentado por prensa de referencia y queda pendiente de contraste con una fuente primaria. La ficha lo advierte expresamente. |

**Gravedad**

| Nivel | Criterio |
|---|---|
| Alta | Daño real a personas o terceros, afectación de derechos fundamentales o capacidad demostrada de causar daño grave, entendida como conducta observada de forma robusta (en varios modelos o sin inducción) que permitiría eludir el control humano. |
| Media | Daño limitado o reversible, o riesgo serio observado en pruebas. |
| Baja | Sin daño real y conducta poco frecuente o muy inducida. |

**Contexto**

| Código | Significado |
|---|---|
| `D` | Uso real (despliegue) |
| `E` | Evaluación o investigación |
| `E→D` | Evaluación con efectos externos |

**Tipología**

| Código | Tipo | Contenido |
|---|---|---|
| C1 | Engaño estratégico | Maquinación, falsa alineación, infrarrendimiento deliberado y ocultación de errores. |
| C2 | Autopreservación | Resistencia al apagado, autoexfiltración, chantaje y protección de otros modelos. |
| C3 | Hackeo de recompensa | Trampas en pruebas o evaluaciones; cumplimiento de la letra y no del fin de la tarea. |
| C4 | Extralimitación agéntica | Acciones no autorizadas o destructivas, escape de entornos y uso de credenciales ajenas. |
| C5 | Complacencia y manipulación | Adulación, refuerzo de delirios, dependencia emocional y autolesiones. |
| C6 | Valores en contenidos | Discurso de odio, sesgo ideológico, sexualización y sesgos políticos incrustados. |
| C7 | Desalineación emergente | Generalización indebida a partir de un ajuste fino o del hackeo de recompensa. |
| C8 | Opacidad y conciencia de evaluación | Razonamiento infiel u ofuscado; conducta distinta cuando el modelo cree estar en una prueba, o cuando da por simulado un entorno real. La ocultación de acciones ante usuarios o supervisores se clasifica en C1. |
| C9 | Colusión entre agentes | Canales no autorizados y cooperación entre instancias para eludir controles. |

## Inventario de fallos de gobernanza

`gobernanza.csv` recoge los **fallos de gobernanza interna** de los laboratorios: decisiones u omisiones organizativas del desarrollador (o de sus evaluadores y proveedores) que producen o permiten conductas dañinas de sus sistemas, o que incumplen compromisos de seguridad declarados, sin que la causa sea que el modelo persiga por su cuenta otra conducta. Un mismo hecho puede tener una dimensión de desalineación (ficha MA-xx) y otra de gobernanza (ficha GOB-xx); la columna `casos_relacionados` las enlaza.

**Tipos**

| Código | Tipo | Contenido |
|---|---|---|
| G1 | Control de cambios y accesos internos | Modificaciones no autorizadas de prompts, pesos, código o configuraciones; accesos indebidos de empleados o contratistas. |
| G2 | Evaluación y decisión de despliegue | Lanzar sin evaluar, pese a advertencias o con plazos de prueba insuficientes. |
| G3 | Contención de pruebas y entornos | Entornos de evaluación o entrenamiento mal aislados, salvaguardas desactivadas, perímetro de acciones mal definido; propios o externalizados. |
| G4 | Integridad de activos | Filtración o exposición de pesos, código, credenciales o infraestructura. |
| G5 | Transparencia y compromisos | Fichas técnicas ausentes o tardías; incumplimiento de marcos de seguridad o compromisos voluntarios. |
| G6 | Políticas internas contrarias a los valores declarados | Normas internas que permiten conductas que el laboratorio dice rechazar. |
| G7 | Detección, escalado y notificación | Detección tardía, escalado interno débil, notificación tardía o discrecional a afectados y autoridades, canales de alerta. |
| G8 | Datos personales en entrenamiento y evaluación | Uso o exposición de datos personales en entornos de agentes, entrenamiento o evaluación. |

**Columnas propias:** `actor` (quién incurre en el fallo), `autor_fallo` (`Laboratorio`, `Evaluador` o `Proveedor`), `sistema`, `tipos` (G1–G8), `atribucion` (si la causa la verifica un tercero o solo la afirma el laboratorio) y `casos_relacionados`. El resto de columnas sigue los criterios de este README, incluido el estado de verificación.

**Estado:** prototipo en desarrollo, versión inicial (26 oct. 2026). Las fichas están pendientes de segunda revisión; la web las muestra en la pestaña «Gobernanza» desde el 27 oct. 2026, señalada como prototipo en desarrollo y con un aviso de versión inicial (constante `AVISO_GOB` de `index.html`, que se vacía al terminar la revisión).

**Alcance y límites.** El inventario recoge fallos de gobernanza interna documentados en fuentes públicas hasta la fecha de actualización. No pretende ser exhaustivo ni representativo, y el número de fichas por actor no permite comparar la frecuencia de fallos entre laboratorios: depende de la información que cada uno publica (informes, fichas técnicas, comunicaciones de incidentes) y de la atención que reciben de evaluadores y prensa. La ausencia de fichas de un actor no implica que no existan fallos. Las fichas con estado «En desarrollo (información periodística)» están pendientes de contraste con una fuente primaria, y todo el inventario está pendiente de segunda revisión.

**Números retirados del inventario de gobernanza:** GOB-01, GOB-03, GOB-12 y GOB-23 (descartadas en la revisión del 27 oct. 2026 por no cumplir los criterios de inclusión). Los números no se reutilizan.

## Estructura de los datos

`incidentes.csv` usa punto y coma (`;`) como separador y codificación UTF-8. Los campos con varios valores se separan con barra vertical (`|`).

| Columna | Contenido | Ejemplo |
|---|---|---|
| `id` | Identificador único | `MA-34` |
| `fecha` | Fecha tal como se muestra | `may.–jul. 2026` |
| `orden` | Fecha para ordenar (`AAAA-MM`, con letra si hay varios en el mismo mes) | `2026-07a` |
| `laboratorios` | Laboratorios o desarrolladores | `OpenAI\|Anthropic` |
| `modelo` | Modelo o sistema implicado | `GPT-5.6 Sol` |
| `titulo` | Título breve del caso | |
| `categorias` | Códigos de tipología | `C3\|C4` |
| `contexto` | `D`, `E` o `E→D` | `E→D` |
| `gravedad` | `Alta`, `Media` o `Baja` | `Alta` |
| `nota_gravedad` | Justificación de la gravedad | |
| `discutido` | `sí` si los hechos o la causalidad están en discusión | `no` |
| `descripcion` | Descripción del caso | |
| `evidencia` | Fuente principal | |
| `url` | Enlace a la fuente principal | |
| `verificacion` | `Verificado` o `En desarrollo (información periodística)` | `Verificado` |
| `respuesta` | Respuesta del laboratorio | |
| `relevancia_ue` | Relevancia en el marco jurídico de la UE | |

## Cómo actualizar el inventario

1. Abre `incidentes.csv` en GitHub (icono del lápiz) o descárgalo y edítalo en Excel.
2. Añade una fila por caso nuevo o corrige la existente, siguiendo la estructura anterior.
3. Si usas Excel, guarda como **CSV UTF-8** para conservar los acentos.
4. Sube el archivo al repositorio y confirma el cambio (*Commit changes*).

La web se actualiza sola en uno o dos minutos, incluida la fecha de última actualización.

## Cómo citar

> Hernández Peña, J. C. y Polanco, J. (dirs.) (2026). *Inventario de casos de desalineación en IA de frontera*. Observatorio de PrivaIA Lab Navarra, Facultad de Derecho, Universidad de Navarra. Disponible en: https://hernandezpena.github.io/misalignment/ [consulta: fecha].

## Autoría

Elaborado por el Observatorio de **PrivaIA Lab Navarra**, grupo de investigación vinculado a la Facultad de Derecho y al Instituto de Ciencia de los Datos e Inteligencia Artificial (DATAI) de la Universidad de Navarra, inscrito como grupo de excelencia en la Agencia Española de Protección de Datos (AEPD).

**Dirección:** Juan Carlos Hernández Peña, Profesor Titular de Derecho Administrativo de la Universidad de Navarra, y Joslay Polanco, profesora de la Universidad Internacional de La Rioja (UNIR).

Este inventario se enmarca en el proyecto de investigación **MODERA**, «Moderación algorítmica y reconfiguración de los derechos fundamentales en la era de la IA generativa» (convocatoria PIUNA 2025-26, Universidad de Navarra), del que son investigadores principales Juan Carlos Hernández Peña y Pablo Castillo Rovira. Forma parte, asimismo, de la línea de investigación prioritaria [«Información, regulación y transición digital al servicio de la verdad»](https://www.unav.edu/conoce-la-universidad/estrategia-2530/ciencia) de la Estrategia 25/30 de la Universidad de Navarra.

## Licencia

Los datos y los contenidos de este inventario se publican bajo licencia [Creative Commons Atribución 4.0 Internacional (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.es): pueden reutilizarse para cualquier fin, citando la fuente.
## Registro de cambios

| Fecha | Cambio | Motivo |
|---|---|---|
| 2026-10-20 | Organización del Proyecto en tres tipos de hilo | Evitar pérdida de contexto en hilos largos |
| 2026-10-20 | Ficha única y estado de verificación | Unificar plantilla, chuleta y web |
| 2026-10-20 | Criterio sobre jailbreaks | Completar los criterios de inclusión |
| 2026-10-26 | Criterios: exclusión de salidas aisladas y excepciones; definición de C8; criterio de gravedad Alta | Decisiones de la dirección |
| 2026-10-26 | Fichas MA-40 a MA-44; MA-13 dividida (MA-43); MA-17 trasladada a gobernanza; actualización de fuentes y correcciones | Vigilancia semanal y revisión de fuentes |
| 2026-10-26 | Inventario de fallos de gobernanza (`gobernanza.csv`, versión inicial) | Separar la gobernanza de la desalineación |
| 2026-10-27 | Pestaña «Gobernanza» en la web (`index.html`): resumen, distribución por tipo, filtros, fichas y enlaces cruzados MA–GOB; párrafo «Alcance y límites» de gobernanza (README y web); la sección se señala como prototipo en desarrollo; correcciones mínimas de `gobernanza.csv` (enlace de GOB-24, respuesta de GOB-03 y GOB-07, referencias al RIA anteriores a su aplicabilidad, fuentes de GOB-09 y GOB-11); se elimina del README una línea suelta de enlace a un adjunto | Hacer visible el inventario de gobernanza |
| 2026-10-27 | Revisión de gobernanza (primer lote): se retiran GOB-01, GOB-03, GOB-12 y GOB-23; GOB-09 reformulada (solo G4, atribución y respuesta corregidas, relevancia UE condicionada); MA-17 vuelve a `incidentes.csv` como caso controvertido y GOB-16 queda como ficha de su dimensión organizativa | Aplicación del protocolo de revisión de gobernanza |
| 2026-10-27 | Auditoría de lo publicado: GOB-24 (hechos atenuados según la fuente; se quita G4); GOB-30 y MA-37 (relevancia RGPD condicionada, sin afirmar incumplimiento); salvedad de aplicabilidad del RIA en MA-01, 02, 03, 08, 12, 13, 15, 19 y 43 | Coherencia con el criterio aplicado a GOB-09 y al resto de fichas de gobernanza |
