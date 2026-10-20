[README.md](https://github.com/user-attachments/files/33708503/README.md)
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
| `incidentes.csv` | Datos del inventario: una fila por caso. Es el único archivo que se actualiza. |
| `README.md` | Este documento. |

La página lee `incidentes.csv` y genera automáticamente el cuadro resumen, los gráficos, el mapa de calor y las fichas de casos.

## Criterios del inventario

**Definición.** Se entiende por desalineación que un sistema de IA persiga de forma sistemática un objetivo o una conducta distinta de la pretendida por quienes legítimamente lo dirigen, o contraria a los valores que declara el propio laboratorio. Se excluyen el uso malicioso por terceros y los errores factuales aislados.

**Fuentes**, por orden de preferencia: documentación de los laboratorios (fichas técnicas, informes y artículos), evaluaciones de terceros independientes, resoluciones y procedimientos públicos, y periodismo de investigación. Los casos con hechos o causalidad en discusión se marcan como controvertidos.

**Gravedad**

| Nivel | Criterio |
|---|---|
| Alta | Daño real a personas o terceros, afectación de derechos fundamentales o capacidad demostrada de causar daño grave. |
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
| C8 | Opacidad y conciencia de evaluación | Razonamiento infiel u ofuscado; conducta distinta cuando el modelo detecta la prueba. |
| C9 | Colusión entre agentes | Canales no autorizados y cooperación entre instancias para eludir controles. |

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
