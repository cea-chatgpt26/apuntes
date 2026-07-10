# Día 12 — Make I: primera automatización

**Módulo 3 · Aplicaciones Prácticas de ChatGPT**

---

## Recapitulando el día anterior

Rápido:

> **¿Qué diferencia hay entre automatización y aumento cuando la IA cambia una tarea de tu trabajo?**

Si lo recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 11 antes de continuar.

---

## De hablar con la IA a que la IA trabaje sola

Todo lo que has hecho hasta ahora en el curso tiene algo en común: **tú abres una herramienta, escribes, y lees el resultado**. Aunque el día 9 viste agentes que actúan por su cuenta, siempre había alguien iniciando la conversación.

Hoy cambia eso. Vas a construir un sistema que se dispara solo, hace su trabajo, y te entrega el resultado sin que tengas que abrir nada. Eso es una **automatización**, y **Make** es la herramienta con la que la vas a construir — sin escribir una sola línea de código.

Esto no es un ejercicio teórico: hoy arranca tu **proyecto del curso**, una automatización con IA + Make que te servirá como pieza de portfolio para enseñar a un futuro empleador. Primero practicas el mecanismo con un ejemplo guiado, y al final del día eliges tu propia idea y le aplicas todo lo aprendido. El mini-proyecto se construye en los próximos tres días (12-14) y forma parte de lo que presentarás el día 20.

---

## Qué es Make

**Make** (antes Integromat) es una herramienta de automatización visual: en lugar de programar, conectas cajas en un lienzo y decides qué información pasa de una a otra. Cuando algo ocurre (llega un email, alguien rellena un formulario), Make ejecuta la cadena de pasos que le hayas diseñado, automáticamente.

**Por qué Make y no otra herramienta:**

| Herramienta | Por qué la descartamos (o no) |
|---|---|
| **Zapier** | Referencia del sector, pero el plan gratuito es muy limitado y se encarece rápido |
| **n8n** | Potente y gratuito si te lo instalas tú mismo, pero requiere más conocimiento técnico para empezar |
| **Make** | Plan gratuito generoso, interfaz visual muy intuitiva y **nodo nativo de ChatGPT/OpenAI** — la razón principal por la que lo usamos en este curso |

---

## El vocabulario básico de Make

Antes de tocar la interfaz, cuatro conceptos que vas a usar todo el rato:

| Concepto | Qué es | Analogía |
|---|---|---|
| **Escenario (scenario)** | Una automatización completa, de principio a fin | Una receta de cocina completa |
| **Módulo (module)** | Cada caja individual dentro del escenario — una acción o una app conectada | Un paso de la receta |
| **Disparador (trigger)** | El primer módulo: el evento que arranca todo el escenario | "Cuando llegue un pedido..." |
| **Conexión (connection)** | El enlace entre dos módulos por el que viaja la información | La flecha que une un paso con el siguiente |

Un escenario siempre sigue la misma lógica: **algo ocurre → Make hace algo con ello → entrega un resultado.**

---

## El lienzo de Make

Cuando entras en un escenario nuevo, ves un lienzo (canvas) vacío con un único botón: añadir el primer módulo, que siempre es el disparador. A partir de ahí:

- Cada módulo nuevo se añade con el icono **+** a la derecha del anterior
- Las líneas entre módulos muestran el orden de ejecución
- El botón **Run once** ejecuta el escenario una sola vez, para probarlo mientras lo construyes — así no tienes que esperar a que se dispare solo
- Cada vez que ejecutas el escenario, Make guarda un registro (**historial**) de qué pasó en cada módulo — fundamental para depurar cuando algo falla

**Ojo con esto:** mientras construyes y pruebas, el escenario está **desactivado** por defecto. No se ejecuta solo hasta que tú lo actives explícitamente (interruptor arriba a la izquierda). Es una medida de seguridad — no vas a mover datos reales sin querer mientras aprendes.

---

## Los disparadores más comunes

El disparador define cuándo arranca tu automatización. Los tres tipos que vas a usar en este curso:

| Tipo de disparador | Cuándo se usa | Ejemplo |
|---|---|---|
| **Webhook** | Cuando otra app o formulario avisa a Make en el momento en que ocurre algo | Alguien rellena un Google Form |
| **Watch (vigilancia)** | Make revisa periódicamente una app por si hay algo nuevo | Revisar la bandeja de Gmail cada 15 min por si llega un email nuevo |
| **Programado (scheduled)** | Se dispara a una hora fija, sin depender de ningún evento externo | Todos los días a las 8:00 |

Para tu primera automatización de hoy vas a usar un **webhook** o un **watch**, según la idea de tu proyecto — son los más fáciles de probar en clase porque puedes disparar el evento tú mismo.

---

## Construyendo tu primera automatización

El objetivo de hoy es simple a propósito: un escenario de **dos o tres módulos** que funcione de principio a fin. Nada de lógica condicional ni IA todavía — eso llega mañana.

**Estructura mínima:**

1. **Disparador:** algo que puedas provocar tú mismo en clase (rellenar un formulario, enviarte un email, añadir una fila a una hoja de cálculo)
2. **Acción:** qué hace Make con ese dato (guardarlo en otro sitio, enviarte una notificación)

**Ejemplo guiado (el que vas a replicar en clase):**

> Formulario de Google Forms → nuevo módulo de Google Sheets que añade una fila con la respuesta.

Este flujo no usa IA todavía a propósito: el objetivo de hoy es que entiendas el mecanismo — disparador, módulo, conexión, mapeo de datos — antes de meter ChatGPT en la ecuación mañana.

### Mapear datos entre módulos

Lo más importante que vas a aprender hoy: cuando conectas un módulo a otro, Make te deja **arrastrar campos del módulo anterior** (nombre, email, fecha...) al módulo siguiente. Eso es "mapear datos" — le dices a Make exactamente qué dato de un paso usar en el siguiente, en vez de escribirlo a mano. Es la base de todo lo que construirás el resto del curso.

---

## Ejercicio 1 — Crea tu cuenta y explora el lienzo

Crea tu cuenta gratuita en Make. Antes de construir nada, dedica 5 minutos a explorar el lienzo: dónde está el botón de añadir módulo, dónde está "Run once", dónde se ve el historial de ejecuciones.

---

## Ejercicio 2 — Construye el escenario guiado

Replica el flujo del ejemplo: **Google Forms → Google Sheets**. Rellena el formulario de prueba y usa "Run once" para comprobar que la fila aparece correctamente en la hoja.

<details>
<summary>Si algo falla</summary>

- Revisa el historial de ejecución: Make te dice en qué módulo se cortó y por qué
- El error más común es no tener autorizada la conexión con la app (Google, en este caso) — Make te lo pide la primera vez que usas cada módulo
- Si el dato no llega mapeado, revisa que arrastraste el campo correcto del módulo anterior, no que lo escribiste a mano

</details>

---

## Trabajo en equipo — Carrera de automatizaciones

*(30 minutos)*

### El reto

En parejas, cada equipo recibe un disparador distinto (formulario, email programado, nueva fila en hoja de cálculo) y debe construir el escenario de dos módulos más rápido posible, probándolo con "Run once" hasta que funcione sin errores.

### Puesta en común

Cada pareja enseña su escenario funcionando en directo. Comentad:
- ¿Qué error os costó más resolver?
- ¿Qué disparador os pareció más fácil de probar en clase, y cuál más útil en un caso real?
- De los disparadores que habéis visto hoy, ¿cuál creéis que encajará mejor con el proyecto que vais a elegir al final del día?

---

## Elige tu proyecto

*(30 minutos)*

Ya conoces el mecanismo — disparador, módulo, conexión, mapeo de datos. Ahora te toca elegir la idea de tu **proyecto del curso**: una automatización con IA + Make que te servirá como pieza de portfolio para enseñar a un futuro empleador. Es un proyecto libre — puede estar orientado a buscar empleo o a cualquier otro problema real del sector al que quieras volver.

**Ideas para inspirarte** (elige una, adáptala a tu sector, o propón la tuya siguiendo el mismo patrón):

| Idea | Problema que resuelve | Qué generaría la IA |
|---|---|---|
| **Respuesta automática de atención al cliente** | Consultas repetitivas por email/WhatsApp que consumen tiempo | Respuestas de texto adaptadas a cada consulta |
| **Generador y publicador de contenido para redes** | Crear y publicar contenido de forma constante | Textos e imágenes para publicaciones |
| **Triage de leads/emails entrantes** | Clasificar manualmente cada entrada según urgencia o tipo | Clasificación y borrador de respuesta |
| **Informe periódico automático** | Recopilar y resumir datos a mano cada semana | Resumen del informe en lenguaje natural |
| **Onboarding automatizado** | Dar la bienvenida y explicar los primeros pasos a cada cliente/empleado nuevo | Mensajes de bienvenida y contenido personalizado |
| **Asistente de búsqueda de empleo** | Filtrar ofertas, adaptar CV/carta a cada oferta o preparar entrevistas | CV, cartas o preguntas de entrevista adaptadas a cada caso |

> *Consejo:* si te interesa un sector concreto (hostelería, comercio, administración, sanidad...), adapta el ejemplo del problema a ese sector — el proyecto pesa más en una entrevista si demuestra que entiendes el día a día de ese trabajo.

Consulta el menú completo, la plantilla de brief y el calendario de fases en [proyecto-final.md](../proyecto-final.md). Rellena el brief de una página — no hace falta que sea definitivo, pero necesitas saber qué quieres automatizar antes de seguir con Make II mañana.

Por último, aplica lo aprendido hoy a tu propia idea: **¿qué dispara tu automatización en la vida real** (un formulario, un email, una hoja de cálculo) **y qué acción dispara ese evento?** No hace falta construirlo todavía — con dejarlo definido en el brief es suficiente. Mañana (día 13) añades el nodo de OpenAI y la lógica condicional, así que el escenario seguirá creciendo.

---

## Lo que aprendiste hoy

- Hoy arrancó tu proyecto del curso: al final del día elegiste una idea y escribiste el brief, ya con el mecanismo de Make aprendido
- Make automatiza tareas conectando módulos en un lienzo visual, sin escribir código
- Un escenario siempre sigue la lógica: disparador → módulo(s) → resultado
- Los tres disparadores más comunes son webhook, watch (vigilancia periódica) y programado
- "Run once" te deja probar el escenario paso a paso mientras lo construyes, sin esperar a que se dispare solo
- Mapear datos es arrastrar un campo de un módulo anterior al siguiente, en vez de escribirlo a mano — es la base de cualquier flujo en Make

---

*Mañana: Make II — añades el nodo de OpenAI y lógica condicional a tu automatización.*
