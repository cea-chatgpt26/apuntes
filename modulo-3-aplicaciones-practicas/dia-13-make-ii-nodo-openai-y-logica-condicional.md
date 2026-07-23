# Día 13 — Make II: nodo OpenAI y lógica condicional

**Módulo 3 · Aplicaciones Prácticas y Proyecto**

---

## Recapitulando el día anterior

Rápido:

> **¿Cuál es la diferencia entre usar un Router y usar un Filter en Make?**

Si lo recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 12 antes de continuar.

---

## De automatizar acciones a automatizar decisiones con IA

Ayer construiste escenarios que mueven datos y, como mucho, los enrutan según una condición simple (un número, una palabra en el asunto, una fecha). Eso cubre mucho, pero tiene un límite: **si la condición no es simple** — si depende de entender el tono de un mensaje, resumir un texto largo, o decidir algo que no cabe en una regla fija — un Filter o un Router no llegan.

Hoy resuelves eso metiendo un **módulo de OpenAI** dentro del escenario. En vez de "si el asunto contiene la palabra X", el flujo pregunta a un modelo de lenguaje "¿de qué trata este mensaje?" y usa la respuesta para decidir el siguiente paso. Es la pieza que convierte tus escenarios de ayer en algo mucho más parecido al agente que viste en el día 9.

---

## El módulo de OpenAI en Make

Añadir IA a un escenario es, mecánicamente, añadir un módulo más — no distinto en la forma a los que ya usaste ayer, solo con un comportamiento distinto por dentro:

| | Módulo normal (ayer) | Módulo de OpenAI |
|---|---|---|
| **Qué hace** | Una acción fija: guardar, enviar, crear... | Recibe un texto (el prompt) y devuelve una respuesta generada por el modelo |
| **Entrada** | Datos concretos: un email, un nombre, un número | Un prompt, normalmente combinando texto fijo + datos que vienen de módulos anteriores |
| **Salida** | Un resultado estructurado y predecible | Texto generado — hay que decidir qué hacer con él después |

Para conectarlo necesitas una **API key de OpenAI** (se configura como conexión, igual que conectaste Gmail o Sheets ayer). El módulo más habitual es **"Create a Chat Completion"** o equivalente: le das un prompt (con **rol** e **instrucciones**, como en el día 4) y te devuelve el texto generado, listo para usar en el siguiente módulo del escenario.

---

## Cómo escribir el prompt dentro de un módulo

La diferencia clave frente a escribir un prompt en ChatGPT es que aquí **el prompt combina texto fijo que tú escribes con datos que vienen de módulos anteriores** (el asunto de un email, el contenido de una fila, el nombre de un cliente...). Esos datos se insertan como variables — se ven como una "burbuja" azul dentro del campo de texto, no como texto plano.

Ejemplo de estructura de prompt dentro de un módulo:

```
Eres un asistente que clasifica mensajes de atención al cliente.

Clasifica el siguiente mensaje en una sola palabra: URGENTE, NORMAL o SPAM.
Responde solo con esa palabra, sin explicación.

Mensaje: {{contenido del email del módulo anterior}}
```

Dos cosas que marcan la diferencia entre que el resto del escenario funcione o se rompa:

- **Pide un formato de salida estricto.** Si el siguiente módulo necesita leer la respuesta (por ejemplo, para decidir una ruta), un texto libre es difícil de procesar — pide una palabra, un número o un JSON concreto, no un párrafo.
- **Usa pocos-ejemplos (few-shot, día 4) si la clasificación es ambigua.** Cuantos más ejemplos le des dentro del prompt, más consistente será la respuesta cada vez que se ejecute el escenario.

---

## Lógica condicional con IA: el Router se vuelve inteligente

Ayer un Router decidía la ruta mirando un dato tal cual llegaba (un número, una palabra exacta). Hoy, el dato que mira el Router puede ser **la respuesta generada por el módulo de OpenAI**, así que el escenario puede tomar decisiones que antes eran imposibles con reglas fijas:

> Email recibido → módulo OpenAI clasifica el tono/tema → Router: si dice "URGENTE" → ruta A, si dice "NORMAL" → ruta B, si dice "SPAM" → ruta C

La lógica del Router no cambia respecto a ayer — sigue siendo un filtro sobre un dato. Lo que cambia es que **ese dato ahora lo decide un modelo, no una regla que tú escribiste a mano**. Esto es exactamente el salto de "chatbot" a "agente" que viste en el día 9: el sistema decide un paso basándose en lo que interpreta, no en una condición rígida.

---

## Antes de empezar: prueba guiada

Añade un módulo de OpenAI a un escenario simple (puede ser el que montaste ayer). Dale un texto de entrada fijo o de un módulo anterior, pídele una clasificación en una sola palabra, y comprueba con **Run once** que la respuesta llega limpia (sin texto sobrante) al siguiente módulo.

<details>
<summary>Si la respuesta viene "sucia" (con explicaciones o texto extra)</summary>

Ajusta el prompt: sé más explícito ("responde ÚNICAMENTE con una de estas palabras: X, Y, Z, sin nada más") y baja la temperatura del modelo si la opción está disponible en el módulo — respuestas más deterministas, menos variación entre ejecuciones.

</details>

---

## Catálogo de ejercicios — elige tu ruta

Igual que ayer: no hace falta hacerlos todos. Elige al menos uno de Nivel 1, uno de Nivel 2, y si te sobra tiempo, prueba uno de Nivel 3. Intenta que al menos uno se parezca al problema real de tu mini-proyecto.

### Nivel 1 — Un módulo de OpenAI, sin condición

El objetivo es soltura básica con el prompt dentro del módulo: generar o transformar un texto y pasarlo al siguiente paso.

| Ámbito | Automatización a construir |
|---|---|
| **Atención al cliente** | Nuevo email recibido → IA genera un resumen de una línea → se guarda en una hoja de seguimiento |
| **Ventas / CRM** | Nuevo lead con una descripción larga → IA genera un resumen ejecutivo de 2 líneas → se añade a la hoja de leads |
| **Marketing / redes** | Título de producto en una hoja → IA genera una descripción corta para redes → se guarda en la columna siguiente |
| **RRHH** | CV recibido (texto pegado o extraído) → IA genera un resumen del perfil en 3 líneas → se guarda en la hoja de candidatos |
| **Administración** | Texto de una factura o albarán → IA extrae el importe total y el proveedor → se añaden como columnas nuevas en la hoja |
| **Educación / formación** | Pregunta de un alumno por formulario → IA genera un primer borrador de respuesta → se guarda para que el profesor lo revise antes de enviarlo |

<details>
<summary>Qué comprobar al terminar</summary>

- El texto generado llega completo y sin cortar al siguiente módulo
- Si el prompt pide un formato concreto (una línea, un número), la IA lo respeta la mayoría de las veces — si falla a menudo, el prompt necesita ser más estricto

</details>

---

### Nivel 2 — Módulo de OpenAI + Router condicional

Aquí la respuesta de la IA no solo se guarda, sino que **decide la ruta** que sigue el escenario.

| Ámbito | Automatización a construir |
|---|---|
| **Atención al cliente** | Email recibido → IA clasifica en URGENTE / NORMAL / SPAM → Router: urgente notifica al canal prioritario, normal se registra, spam se descarta |
| **Ventas / CRM** | Nuevo lead con mensaje libre → IA clasifica el nivel de interés (ALTO / MEDIO / BAJO) → Router: alto interés notifica a ventas de inmediato, el resto se archiva para seguimiento |
| **Marketing / redes** | Comentario recibido en redes (pegado manualmente o vía formulario) → IA clasifica el sentimiento (POSITIVO / NEGATIVO / NEUTRO) → Router: negativo se escala a un responsable, el resto se archiva |
| **RRHH** | CV recibido → IA valora si el perfil encaja con el puesto (SÍ / NO / REVISAR) → Router: encaja pasa a la siguiente fase, no encaja se descarta con email automático, revisar se marca para un humano |
| **Administración** | Factura recibida → IA extrae el importe → Router: si supera un umbral se envía a validación manual, si no se archiva directamente |
| **Logística / inventario** | Incidencia de pedido descrita por texto libre → IA clasifica el tipo (RETRASO / DAÑO / ERROR DE ENVÍO) → Router: cada tipo sigue un camino de gestión distinto |

<details>
<summary>Dónde se suele atascar la gente en este nivel</summary>

- El Router compara texto exacto: si el prompt a veces devuelve "Urgente" y otras "URGENTE" o "urgente.", el filtro no coincide — fuerza mayúsculas/minúsculas exactas en el prompt y, si puedes, usa condiciones que ignoren mayúsculas
- Olvidar poner una ruta por defecto ("Fallback") para cuando la IA devuelve algo inesperado

</details>

---

### Nivel 3 — Encadenar dos llamadas a la IA

Un módulo de OpenAI puede alimentar a otro: el primero clasifica o extrae, el segundo genera contenido usando ese resultado.

| Ámbito | Automatización a construir |
|---|---|
| **Atención al cliente** | Email clasificado como URGENTE → segundo módulo de IA genera un borrador de respuesta empática y concreta → se guarda como borrador, no se envía solo |
| **Ventas / CRM** | Lead clasificado como ALTO interés → segundo módulo de IA genera un email de seguimiento personalizado con los datos del lead → se guarda para revisión del comercial |
| **Marketing / redes** | Producto con descripción generada (Nivel 1) → segundo módulo de IA genera 3 variantes de titular para probar cuál funciona mejor |
| **RRHH** | CV marcado como "encaja" → segundo módulo de IA genera 3 preguntas de entrevista específicas para ese perfil |
| **Administración** | Factura con datos extraídos → segundo módulo de IA redacta un email breve de confirmación de recepción al proveedor |
| **Educación / formación** | Pregunta de alumno respondida por IA (Nivel 1) → segundo módulo de IA revisa esa respuesta y señala si contiene algo que debería verificar un humano (recuerda el día 3: alucinaciones) |

<details>
<summary>Pista técnica</summary>

Cada módulo de OpenAI es independiente: el prompt del segundo módulo puede referenciar tanto el dato original (el email, el CV) como la salida del primer módulo de IA. Igual que ayer encadenabas módulos normales, hoy encadenas "razonamientos" — pero cada eslabón sigue siendo tan bueno como el prompt que le has dado.

</details>

---

### Nivel 4 (reto opcional) — Router inteligente de tres o más rutas

Diseña un escenario con un módulo de OpenAI que clasifique en **al menos tres categorías**, cada una llevando a una acción distinta y real (no solo un registro en una hoja para las tres). Añade una ruta de "fallback" por si la respuesta de la IA no encaja en ninguna categoría esperada.

<details>
<summary>Cómo elegir el caso</summary>

Piensa en una tarea de tu trabajo donde hoy decides "a mano" en qué categoría cae algo antes de actuar (una consulta, una solicitud, un ticket) — ese es el patrón exacto que hoy puedes delegar a la IA dentro de Make.

</details>

---

## Conecta esto con tu mini-proyecto

Vuelve al trigger que montaste ayer para tu mini-proyecto y añade un módulo de OpenAI que haga algo útil con ese dato: clasificarlo, resumirlo o generar un texto a partir de él. No hace falta que sea la versión final — el objetivo es que el flujo ya tenga IA dentro antes del día 14.

<details>
<summary>Qué apuntar</summary>

- ¿Qué decide o genera la IA en tu flujo?
- ¿El resultado necesita revisión humana antes de actuar, o puede disparar la siguiente acción automáticamente?

</details>

---

## Trabajo en equipo — Reto por parejas

*(25 minutos)*

### El reto

En parejas, elegid **un ejercicio de Nivel 2 o Nivel 3 del catálogo** (de un ámbito distinto al de vuestro propio proyecto) y construidlo completo en Make antes de que se acabe el tiempo, incluyendo el Router condicional.

### Puesta en común

- ¿Qué prompt usasteis para que la clasificación fuera consistente?
- ¿Tuvisteis que ajustar el prompt más de una vez porque el Router no reconocía la respuesta?
- ¿En qué punto del flujo dejaríais que la IA actúe sola, y en qué punto preferiríais que un humano revise antes?

---

## Lo que aprendiste hoy

- El módulo de OpenAI en Make funciona como cualquier otro módulo: recibe datos de entrada y devuelve un resultado, en este caso texto generado
- El prompt dentro de un módulo combina texto fijo con datos de módulos anteriores, insertados como variables
- Pedir un formato de salida estricto (una palabra, un número, un JSON) es lo que permite que el resto del escenario pueda leer la respuesta de la IA
- Un Router puede usar la respuesta de la IA como condición, no solo datos fijos — así el escenario "decide" en lugar de solo "filtrar"
- Se pueden encadenar varios módulos de IA: uno clasifica o extrae, el siguiente genera contenido a partir de ese resultado
- Tu mini-proyecto ya tiene IA dentro del flujo — mañana lo completas con lógica más avanzada

---

*Mañana: Make III — flujos avanzados para cerrar la versión completa de tu mini-proyecto.*
