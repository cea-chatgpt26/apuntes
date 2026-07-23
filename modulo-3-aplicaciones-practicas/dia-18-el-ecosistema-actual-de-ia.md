# Día 18 — El ecosistema actual de IA

**Módulo 3 · Aplicaciones Prácticas y Proyecto**

---

## Recapitulando el día anterior

Rápido:

> **¿Cuál es la diferencia entre automatización y aumento, y cuál de las dos es la más habitual en el uso real de IA hoy?**

Si lo recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 17 antes de continuar.

---

## Ampliando la caja de herramientas

Todo el curso ha girado alrededor de un puñado de herramientas — ChatGPT/Gemini, generadores de imagen y vídeo, Make, Cline. Con eso ya tenéis lo esencial. Pero el ecosistema de IA es mucho más amplio, y hoy conocéis tres herramientas más que resuelven problemas muy concretos que ChatGPT no resuelve bien por sí solo: **buscar con fuentes verificables, trabajar sobre vuestros propios documentos, y convertir texto en una presentación visual**.

Hoy también es el día en que **generáis manualmente los insumos** (textos, imágenes, presentaciones) que necesitará el proyecto grande que construiréis mañana — así que cada herramienta que veis hoy tiene una aplicación directa a vuestro proyecto.

---

## Perplexity: buscar con fuentes verificables

**Perplexity** es un motor de búsqueda potenciado por IA: en lugar de darte una lista de enlaces (como Google) o una respuesta sin citar fuentes (como un chat normal), te da una **respuesta redactada con las fuentes citadas junto a cada afirmación**, para que puedas comprobarla tú mismo.

| | Google | ChatGPT (sin buscar) | Perplexity |
|---|---|---|---|
| **Qué devuelve** | Enlaces que tú revisas | Una respuesta redactada, sin fuentes verificables | Una respuesta redactada, con fuente citada en cada afirmación |
| **Actualidad** | En tiempo real | Limitada a su fecha de entrenamiento (salvo que busque) | En tiempo real |
| **Riesgo de alucinación** | Bajo (tú lees la fuente original) | Alto si no verificas (día 3) | Bajo, pero sigue sin ser cero — comprueba la fuente citada |

Es la herramienta ideal cuando necesitáis un dato reciente y verificable — precios, normativa, cifras de mercado — algo que en el día 3 aprendisteis a desconfiar si venía de un chat sin fuentes.

---

## NotebookLM: trabajar sobre tus propios documentos

**NotebookLM** (de Google) es distinto a un chat normal en un punto clave: **solo responde basándose en los documentos que tú le subes**, no en su conocimiento general. Le subes PDFs, notas, transcripciones o enlaces, y a partir de ahí puedes preguntarle, pedirle resúmenes o incluso generar un resumen en formato audio (un "podcast" generado automáticamente sobre tus documentos).

Por qué importa: reduce mucho el riesgo de alucinación (día 3), porque la IA no se inventa nada fuera de lo que le has dado — y si lo hace, puedes verificarlo directamente contra tu propio documento fuente.

Casos de uso directos para vuestro proyecto: subid vuestro brief (día 10-11) y los apuntes de estos días, y pedidle a NotebookLM que os ayude a redactar la descripción de vuestro proyecto grande basándose únicamente en esa información.

---

## Gamma: de texto a presentación

**Gamma** genera presentaciones (o documentos, o páginas web simples) a partir de una descripción en texto: le dices el tema, la estructura y el tono, y te devuelve un primer diseño completo con texto e imágenes, que luego puedes editar.

Es la herramienta más directamente útil para el día 20: en lugar de montar las diapositivas de vuestra presentación final desde cero, podéis generar una primera versión con Gamma y afinarla — ahorrando el tiempo de maquetación para dedicarlo a preparar cómo contáis vuestro proyecto.

---

## Cómo elegir la herramienta correcta

No son herramientas que compitan entre sí, resuelven problemas distintos:

| Necesitas... | Herramienta |
|---|---|
| Un dato actual y verificable de internet | Perplexity |
| Respuestas basadas solo en tus propios documentos | NotebookLM |
| Una presentación o documento visual a partir de texto | Gamma |
| Generar texto, imagen, vídeo o audio desde cero | Lo visto en los días 2, 4-8 |
| Automatizar un flujo entre aplicaciones | Make (días 12-14) |
| Crear o modificar archivos de un proyecto | Cline (días 15-16) |

---

## Ejercicio 1 — Investiga con Perplexity

Usa Perplexity para investigar un dato reciente relevante para tu sector o tu proyecto (una cifra de mercado, una normativa, una tendencia). Revisa las fuentes citadas.

<details>
<summary>Qué observar</summary>

- ¿Las fuentes citadas son de medios o webs fiables?
- ¿Alguna afirmación no lleva fuente clara? Si es así, trátala con la misma cautela que un dato de ChatGPT sin verificar (día 3)

</details>

---

## Ejercicio 2 — Construye tu notebook con NotebookLM

Sube tu brief de proyecto (día 10-11) y, si los tienes, tus apuntes de los días 12-16, a NotebookLM. Pídele que te ayude a redactar un resumen de tu proyecto en 3-4 frases, basándose solo en esos documentos.

<details>
<summary>Qué comprobar</summary>

¿El resumen que genera se ciñe a lo que pusiste en tus documentos, o añade cosas que no dijiste? Si añade algo que no está en tus fuentes, es una señal de que hay que revisar siempre, incluso con herramientas pensadas para reducir alucinaciones.

</details>

---

## Ejercicio 3 — Genera un insumo real para tu proyecto grande

Usa cualquier herramienta vista en el curso (Gamma, un generador de imágenes del día 7, un generador de audio/vídeo del día 8) para crear **un insumo real** que tu proyecto grande necesitará: una imagen, un texto de bienvenida, un primer borrador de presentación...

<details>
<summary>Por qué este ejercicio importa hoy</summary>

Mañana (día 19) construís el flujo completo en Make integrando estos insumos. Cuanto más preparado llegues hoy, menos tiempo perderás mañana generando contenido sobre la marcha.

</details>

---

## Trabajo en equipo — Duelo de herramientas

*(30 minutos)*

### El reto

En equipos, recibid la misma pregunta de investigación (por ejemplo: *"¿cuáles son las tendencias de contratación en [un sector] para este año?"*). Cada equipo la resuelve con una herramienta distinta: uno con Perplexity, otro con ChatGPT sin buscar, otro con Google tradicional, otro con NotebookLM sobre un documento que se les entrega.

### Puesta en común

- ¿Qué equipo llegó a una respuesta mejor fundamentada, y por qué?
- ¿Dónde se notó más la diferencia: en la actualidad del dato, en las fuentes citadas, o en el tiempo que tardasteis?
- ¿Para qué tipo de pregunta de vuestro trabajo usaríais cada herramienta?

---

## Lo que aprendiste hoy

- Perplexity resuelve el problema de la búsqueda con fuentes verificables, algo que un chat normal no garantiza
- NotebookLM reduce el riesgo de alucinación al responder solo basándose en tus propios documentos
- Gamma convierte una descripción en texto en una presentación o documento visual completo
- Cada herramienta del curso resuelve un problema distinto — elegir bien la herramienta es tan importante como saber usarla
- Ya tienes preparado un insumo real para tu proyecto grande — mañana lo integráis todo en un flujo completo de Make

---

*Mañana: Integración total — construís el proyecto grande completo, con automatización en Make y contenido generado por IA.*
