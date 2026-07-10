# Día 9 — IA para código y agentes

**Módulo 2 · Desafíos y Avances en Inteligencia Artificial**

---

## Recapitulando el día anterior

Rápido:

> **¿Qué elemento de un prompt de vídeo no existe en un prompt de imagen, y por qué es importante especificarlo?**

Si lo recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 8 antes de continuar.

---

## De responder a actuar

Hasta ahora, toda la IA que has usado en el curso hace lo mismo en el fondo: le pides algo y te devuelve un resultado — texto, una imagen, un vídeo, una pista de audio. Tú lees el resultado, decides si te vale, y si no, iteras.

Hoy das un salto conceptual importante: hay un tipo de IA que no solo **responde**, sino que **actúa** — toma un objetivo, decide los pasos necesarios para conseguirlo, usa herramientas por su cuenta (buscar en internet, consultar datos, ejecutar acciones) y solo vuelve a ti cuando tiene un resultado. A esto se le llama **agente**.

No hace falta programar para entender esto ni para usarlo — y es clave para lo que viene en el curso: en el Módulo 3 vais a construir vuestros propios agentes sin código con Make.

---

## Qué es un agente de IA

La diferencia entre un chatbot y un agente no es la marca ni la interfaz, es **cuánto decide por sí mismo**:

| | Chatbot | Agente |
|---|---|---|
| **Qué hace** | Responde a lo que le preguntas | Persigue un objetivo que le das |
| **Pasos** | Un turno = una respuesta | Encadena varios pasos sin que supervises cada uno |
| **Herramientas** | Solo su conocimiento interno (salvo que busque en la web si se lo permites) | Puede buscar, consultar datos, ejecutar acciones, y decidir qué herramienta usar en cada paso |
| **Ejemplo cotidiano** | Le preguntas a un compañero un dato puntual | Le encargas a un compañero "organízame el viaje" y vuelve con vuelo, hotel y itinerario resueltos |

Un ejemplo sencillo para verlo claro:

- **Chatbot:** le preguntas *"¿cuáles son los mejores hoteles en Lisboa?"* y te da una lista basada en lo que sabe.
- **Agente:** le dices *"resérvame un hotel en Lisboa para el 20-22 de agosto, cerca del centro, menos de 100€/noche"* y el agente busca en internet en tiempo real, compara opciones, y te devuelve una reserva lista o una propuesta concreta — sin que tú tengas que ir comparando webs una por una.

La clave no es que sea "más inteligente", es que **actúa en varios pasos con autonomía** sobre un objetivo, en lugar de darte una sola respuesta.

---

## Agentes que ya puedes usar sin programar

Esto es lo que de verdad os interesa hoy: agentes que podéis configurar y usar vosotros mismos, sin escribir una sola línea de código.

### Custom GPTs y Gemini Gems

Tanto ChatGPT como Gemini te permiten crear tu propio asistente personalizado: le das instrucciones fijas (rol, tono, conocimiento, restricciones — como en el día 4) y queda guardado como una herramienta reutilizable. No es un agente completo en el sentido técnico, pero es tu primer paso para "programar" un comportamiento sin código: en lugar de repetir el mismo prompt cada vez, lo dejas configurado una vez y lo usas cuando quieras.

Ejemplos de uso real: un GPT que revisa contratos con tu checklist habitual, uno que responde dudas frecuentes de tu equipo con tu documentación, uno que adapta cualquier texto a tu tono de marca.

### Deep Research (ChatGPT, Gemini, Perplexity)

Este sí es un agente en el sentido completo: le das un tema, y en lugar de responder con lo que ya sabe, **navega por internet en tiempo real, abre varias fuentes, contrasta información y te devuelve un informe estructurado con fuentes citadas** — un proceso que a una persona le llevaría horas.

Es el ejemplo más accesible de "IA que actúa": tú le das el objetivo, el agente decide qué buscar, en qué orden, y cuándo tiene suficiente información para responder.

### Agentes de atención al cliente

Muchas empresas ya usan agentes (no simples chatbots) que resuelven una incidencia de principio a fin: consultan tu pedido en el sistema, gestionan una devolución, actualizan una reserva — sin escalar a una persona salvo que el caso sea complejo. Si alguna vez has hablado con un "chat de soporte" que consultó tu pedido y lo modificó por ti, ya has interactuado con un agente.

**La conexión con lo que viene:** en el Módulo 3 (días 16-19) vais a construir flujos con Make que hacen exactamente esto — dar un objetivo a un sistema y dejar que encadene pasos y herramientas sin que estés supervisando cada uno. Hoy entendéis el concepto; en unas semanas lo vais a construir vosotros.

---

## Y los agentes de código, ¿qué son?

Existe una categoría de agentes pensada para programadores — **GitHub Copilot**, **Cursor** y **Claude Code** son los más conocidos. En una frase cada uno:

- **Copilot:** sugiere código mientras el programador escribe, como un autocompletado muy avanzado.
- **Cursor:** un editor de código pensado desde cero para trabajar con IA, que puede escribir y modificar archivos completos.
- **Claude Code:** un agente que trabaja desde la terminal, capaz de leer un proyecto entero, escribir código, ejecutarlo y corregir sus propios errores sin supervisión paso a paso.

No vais a usar estas herramientas en este curso, pero conviene saber que existen y qué hacen, porque **están cambiando la velocidad y el coste de construir software** — algo que afecta directamente al tema del día 17 (futuro del trabajo con IA), tanto si trabajáis con equipos técnicos como si no.

📺 *Si tenéis curiosidad, buscad en YouTube una demo corta (2-5 min) de "Claude Code" o "Cursor" en acción — no para aprender a usarlo, sino para ver con vuestros propios ojos qué significa que un agente "escriba y ejecute" en vez de solo "responder".*

---

## Ejercicio 1 — Crea tu primer Custom GPT o Gem

Crea un Custom GPT (ChatGPT) o un Gem (Gemini) con un rol concreto y útil para tu trabajo: un revisor de textos con tu tono, un asistente que responde con tu FAQ, un generador de propuestas con tu formato habitual.

<details>
<summary>Qué incluir en la configuración</summary>

- Rol claro (como en el día 4): quién es y para qué sirve
- 2-3 ejemplos de cómo debe responder (few-shot)
- Restricciones: qué no debe hacer o decir

</details>

---

## Ejercicio 2 — Pon a prueba un agente de investigación

Usa Deep Research (o equivalente en Gemini/Perplexity) para investigar un tema relacionado con tu trabajo o sector. Revisa el informe que te devuelve.

<details>
<summary>Qué observar</summary>

- ¿Cita fuentes reales y verificables?
- ¿Hay algún dato que parezca inventado o mal interpretado? (recuerda el día 3: las alucinaciones no desaparecen solo porque el agente "investigue")
- ¿Cuánto tiempo te habría llevado a ti llegar a ese mismo resultado buscando manualmente?

</details>

---


## Trabajo en equipo — El objetivo, no el prompt

*(30 minutos)*

### El reto

Todos los equipos reciben el mismo objetivo de negocio, no un prompt: *"Necesitamos decidir en qué ciudad europea abrir nuestra próxima tienda."*

Cada equipo debe resolverlo con una configuración distinta:

| Equipo | Configuración |
|---|---|
| **Equipo 1** | Un único prompt directo a ChatGPT o Gemini (sin herramientas) |
| **Equipo 2** | Deep Research con un único encargo bien definido |
| **Equipo 3** | Un Custom GPT/Gem configurado previamente con criterios de decisión (población, competencia, coste de alquiler...) + Deep Research |
| **Equipo 4** | Varias preguntas sueltas encadenadas manualmente por el propio equipo (sin agente) |

### Puesta en común

Cada equipo presenta su recomendación final y cómo ha llegado a ella. Comparad:

- ¿Qué equipo llegó a una recomendación más fundamentada?
- ¿Dónde se notó la diferencia entre "preguntar" y "delegar un objetivo"?
- ¿En qué tareas de vuestro trabajo delegaríais un objetivo completo a un agente, y en cuáles preferiríais mantener el control paso a paso?

---

## Lo que aprendiste hoy

- Un agente, a diferencia de un chatbot, persigue un objetivo y encadena pasos por sí solo usando herramientas
- No hace falta programar para usar agentes: Custom GPTs, Gemini Gems y Deep Research ya son agentes accesibles hoy
- Los agentes de código (Copilot, Cursor, Claude Code) siguen la misma lógica aplicada a programar — no los vais a usar, pero están cambiando cómo se construye el software
- Un agente sigue pudiendo alucinar o equivocarse — la autonomía no elimina la necesidad de revisar el resultado
- Este concepto es la base de lo que construiréis en el Módulo 3 con Make: dar un objetivo y dejar que un flujo lo resuelva por vosotros

---

*Mañana: Desafíos éticos — sesgos, privacidad y derechos de autor en la IA.*
