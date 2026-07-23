# Día 16 — Cline II: flujos de trabajo reales

**Módulo 3 · Aplicaciones Prácticas y Proyecto**

---

## Recapitulando el día anterior

Rápido:

> **¿Cuál es la diferencia entre Plan mode y Act mode en Cline, y en qué orden conviene usarlos?**

Si lo recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 15 antes de continuar.

---

## De tareas sueltas a proyectos con memoria

Ayer le diste a Cline instrucciones aisladas, una a una, casi siempre sobre un archivo o dos. Eso funciona para tareas pequeñas, pero un proyecto real tiene más piezas moviéndose a la vez: varios archivos que dependen entre sí, un estilo o unas normas que quieres que se respeten siempre, y la posibilidad de que un cambio salga mal y necesites deshacerlo sin perder todo lo demás.

Hoy añades tres piezas que convierten a Cline de "asistente para una tarea" a "colaborador en un proyecto": cómo darle **contexto** de forma precisa, cómo fijar **reglas propias** que respete en todo momento, y cómo usar los **checkpoints** para retroceder sin miedo.

---

## Contexto preciso: menciones con @

Ayer Cline decidía por sí solo qué archivos mirar. Hoy aprendes a **señalarle exactamente** qué debe tener en cuenta, usando menciones con `@` dentro del chat:

| Mención | Qué le indica a Cline |
|---|---|
| `@archivo.html` | Ten en cuenta este archivo concreto al responder |
| `@carpeta/` | Ten en cuenta todos los archivos de esta carpeta |
| `@problems` | Mira los errores o avisos que el propio editor está marcando ahora mismo |

Por qué importa: cuando un proyecto crece, Cline no siempre adivina qué archivo es relevante para tu petición. Decírselo explícitamente evita que trabaje con información incompleta o que toque un archivo equivocado — el mismo motivo por el que ayer, en el Nivel 3, se recomendaba pedirle que revisara todos los archivos del proyecto antes de proponer un cambio.

---

## Reglas propias: el archivo `.clinerules`

Si quieres que Cline respete siempre las mismas normas (un estilo de código, un idioma, una estructura de carpetas, qué NO debe tocar nunca) sin tener que repetirlo en cada instrucción, se lo dices una vez en un archivo especial: **`.clinerules`**, en la raíz del proyecto. Cline lo lee automáticamente en cada tarea.

Ejemplo de contenido de un `.clinerules`:

```
- Todos los textos visibles deben estar en español.
- No modifiques el archivo config.json bajo ningún concepto.
- Los nombres de archivo van en minúsculas y con guiones, sin espacios.
- Antes de crear un archivo nuevo, comprueba si ya existe algo similar.
```

Es exactamente la misma idea que las **instrucciones fijas de un Custom GPT** (día 9) o el **rol y las restricciones de un buen prompt** (día 4) — solo que aquí se aplican de forma automática a cada tarea dentro de ese proyecto, sin que tengas que volver a escribirlas.

---

## Checkpoints: deshacer sin miedo

Cada vez que Cline aplica un cambio en Act mode, guarda un **checkpoint** — un punto al que puedes volver si el resultado no te convence. Esto es lo que te da margen para pedir cambios ambiciosos sin miedo a "romper" el proyecto: si algo sale mal, retrocedes al checkpoint anterior y lo intentas de otra forma, en vez de deshacer manualmente archivo por archivo.

**La conexión con el día 14:** es la misma lógica que el manejo de errores en Make (Retry, Resume, Break) — no se trata de que todo salga bien a la primera, sino de tener un plan claro para cuando no sale bien.

---

## Antes de empezar: prueba guiada

Coge el proyecto que empezaste ayer (o crea uno nuevo con 2-3 archivos sencillos) y crea un archivo `.clinerules` con al menos dos reglas propias. Pide a Cline una tarea que, sin la regla, probablemente la incumpliría (por ejemplo, si tu regla dice "todo en español", pídele algo de forma ambigua) y comprueba que la respeta.

<details>
<summary>Cómo comprobar que el .clinerules funciona</summary>

Prueba primero sin el archivo `.clinerules` (o con él vacío) y luego con las reglas puestas, pidiendo exactamente la misma tarea las dos veces. Si el resultado cambia y ahora respeta la regla, has confirmado que Cline la está leyendo.

</details>

---

## Catálogo de ejercicios — elige tu ruta

No hace falta hacerlos todos. Elige al menos uno de Nivel 1, uno de Nivel 2, y si te sobra tiempo, prueba uno de Nivel 3.

### Nivel 1 — Contexto preciso con @

| Ámbito | Tarea a pedirle a Cline |
|---|---|
| **Presentación personal / portfolio** | Usando `@` sobre tu página del día 15, pide un cambio que solo afecte a una sección concreta, sin tocar el resto |
| **Documentación** | Usando `@` sobre dos archivos de notas relacionados, pide que un dato se mantenga igual en ambos |
| **Organización personal** | Usando `@` sobre tu lista de tareas, pide que se añada una funcionalidad que dependa de cómo está estructurado el archivo actual |
| **Negocio / freelance** | Usando `@` sobre tu página de menú de servicios y tu página de contacto, pide que ambas compartan el mismo pie de página |
| **Educación / formación** | Usando `@problems`, pide a Cline que revise y corrija cualquier error que el editor esté marcando en tu cuestionario |

<details>
<summary>Qué comprobar al terminar</summary>

- El cambio afectó solo a lo que pediste, no a archivos que no mencionaste
- Si mencionaste varios archivos, el resultado es coherente entre todos ellos

</details>

---

### Nivel 2 — Reglas propias con `.clinerules`

| Ámbito | Tarea a pedirle a Cline |
|---|---|
| **Presentación personal / portfolio** | Regla: mantener siempre una paleta de colores concreta → pide 2-3 cambios de contenido distintos y comprueba que los colores no varían |
| **Documentación** | Regla: todo archivo nuevo debe incluir una fecha de creación en la primera línea → pide que se creen 2 archivos nuevos y comprueba que la regla se cumple en ambos |
| **Organización personal** | Regla: nunca borrar una tarea, solo marcarla como completada → pide "elimina la tarea X" y observa si Cline la marca como completada en vez de borrarla |
| **Negocio / freelance** | Regla: los precios siempre se muestran con dos decimales y el símbolo € → pide añadir un servicio nuevo y comprueba el formato del precio |
| **Educación / formación** | Regla: las preguntas del cuestionario nunca pueden superar las 20 palabras → pide una pregunta nueva sobre un tema y comprueba que la respeta |

<details>
<summary>Dónde se suele atascar la gente en este nivel</summary>

- Escribir reglas demasiado vagas ("que quede bien", "sé cuidadoso") — una regla en `.clinerules` funciona mejor cuanto más verificable es, igual que un buen criterio de few-shot
- Olvidar que las reglas se aplican a partir de que las guardas — no reescriben lo que ya existía antes, salvo que se lo pidas explícitamente

</details>

---

### Nivel 3 — Recuperarse de un cambio no deseado

| Ámbito | Tarea a pedirle a Cline |
|---|---|
| **Presentación personal / portfolio** | Pide un rediseño completo y radical de tu página → si no te convence, usa el checkpoint para volver atrás y pide un cambio más acotado |
| **Documentación** | Pide reestructurar todos tus archivos de notas en un formato distinto → compara el resultado con el checkpoint anterior antes de decidir si te quedas con el cambio |
| **Organización personal** | Pide una función nueva para tu lista de tareas que podría romper la que ya tenías (por ejemplo, ordenar por fecha) → si algo deja de funcionar, retrocede al checkpoint anterior |
| **Negocio / freelance** | Pide reorganizar toda tu página de menú de servicios en un formato de tarjetas → si el resultado no te convence, vuelve atrás y ajusta la instrucción |
| **Educación / formación** | Pide convertir tu cuestionario de una sola página a varias páginas (una por pregunta) → si se rompe la puntuación final, usa el checkpoint para recuperar la versión anterior |

<details>
<summary>Pista técnica</summary>

Los checkpoints aparecen en el propio historial de la conversación con Cline — busca la opción de "restaurar" junto al mensaje del punto al que quieres volver. Practicar esto hoy, con proyectos pequeños y sin riesgo real, es lo que te dará confianza para pedir cambios más ambiciosos en el futuro.

</details>

---

### Nivel 4 (reto opcional) — Proyecto completo con reglas propias

Elige una idea más ambiciosa que las de los días anteriores (por ejemplo, tu página personal + tu lista de tareas + tu menú de servicios, todo en un mismo proyecto con varias páginas enlazadas) y constrúyela definiendo primero un `.clinerules` completo, usando menciones `@` para dar contexto preciso en cada paso, y apoyándote en los checkpoints si algo no sale bien.

<details>
<summary>Cómo saber que lo has conseguido</summary>

Al final, todas las páginas del proyecto deberían compartir un estilo y unas normas coherentes sin que hayas tenido que repetir esas instrucciones en cada mensaje — esa coherencia automática es la señal de que el `.clinerules` está haciendo su trabajo.

</details>

---

## Trabajo en equipo — Rompe y repara

*(25 minutos)*

### El reto

En parejas: una persona define un `.clinerules` con 2-3 reglas y construye una parte del proyecto. Luego, la otra persona (sin ver las reglas) pide a Cline un cambio que probablemente las incumpla. Juntos comprobáis si Cline respetó las reglas o no, y si hace falta, usáis un checkpoint para recuperar la versión correcta.

### Puesta en común

- ¿Cline respetó las reglas del `.clinerules` incluso cuando la instrucción no las mencionaba directamente?
- ¿En qué momento usasteis un checkpoint, y qué habría pasado si no hubierais podido retroceder?
- ¿Qué tipo de reglas creéis que serían más útiles en un proyecto real de vuestro trabajo?

---

## Lo que aprendiste hoy

- Las menciones con `@` permiten señalar a Cline exactamente qué archivos debe tener en cuenta, en vez de dejar que lo adivine
- Un archivo `.clinerules` fija normas que Cline respeta automáticamente en todas las tareas del proyecto, sin repetirlas en cada instrucción
- Los **checkpoints** permiten retroceder a un punto anterior si un cambio no sale como esperabas, sin deshacer todo a mano
- Cuanto más verificable es una regla en `.clinerules`, más fiable es que se cumpla — el mismo principio que un buen criterio de few-shot
- Con contexto preciso, reglas propias y checkpoints, ya tienes las tres piezas para usar Cline en un proyecto real, no solo en tareas sueltas

---

*Mañana: Futuro del trabajo con IA — qué tareas cambian, cuáles desaparecen y cuáles se transforman.*
