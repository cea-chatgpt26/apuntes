# Día 2 — ChatGPT y los Modelos de Lenguaje

**Módulo 1 · Fundamentos de IA y ChatGPT**

---

## Recapitulando el día anterior

Antes de empezar, en 30 segundos:

> **¿Qué diferencia hay entre IA estrecha e IA generativa?**

Si puedes responderlo sin mirar los apuntes, estás listo para hoy.

---

## ¿Qué es un LLM?

LLM son las siglas de **Large Language Model** — Modelo de Lenguaje Grande.

Es el tipo de IA que hay detrás de ChatGPT, Claude, Gemini y otros asistentes de texto.

La idea central es sencilla: un LLM aprende a **predecir la siguiente palabra** en una frase. Eso es todo. Pero hacerlo con cantidades masivas de texto genera algo que parece comprensión, razonamiento y creatividad.

> **Analogía:** es como un músico que ha escuchado millones de canciones. No "entiende" la música de forma emocional, pero puede componer algo que suena coherente y hasta hermoso.

---

## ¿Cómo funciona ChatGPT por dentro?

### 1. El entrenamiento

OpenAI entrenó ChatGPT con una cantidad enorme de texto: libros, artículos, páginas web, código, conversaciones...

El modelo vio patrones en ese texto durante semanas, usando miles de ordenadores trabajando en paralelo. El resultado es una red neuronal con miles de millones de parámetros (como "interruptores" que se ajustan durante el aprendizaje).

### 2. Los tokens

ChatGPT no lee palabras. Lee **tokens** — fragmentos de texto que pueden ser una palabra entera, media palabra o incluso un signo de puntuación.

Ejemplos:
- "hola" → 1 token
- "inteligencia" → 2-3 tokens
- "ChatGPT" → 2 tokens

Esto importa porque los modelos tienen un límite de tokens por conversación (el **contexto**). Cuando una conversación es muy larga, el modelo puede "olvidar" lo que se dijo al principio.

### 3. La temperatura

La temperatura controla la **creatividad vs. precisión** de las respuestas:

| Temperatura baja | Temperatura alta |
|---|---|
| Respuestas más predecibles | Respuestas más creativas |
| Mejor para datos y hechos | Mejor para ideas y brainstorming |
| Menos variación | Más sorpresas |

En ChatGPT no controlas esto directamente, pero puedes pedirlo en el prompt: *"responde de forma creativa"* o *"sé preciso y conciso"*.

---

## Vídeo: cómo funciona ChatGPT

Nate Gentile lo explica de forma muy visual. Ideal para afianzar lo que acabas de leer:

[Nate Gentile — ¿Cómo funciona ChatGPT? La revolución de la IA (50 min)](https://www.youtube.com/watch?v=FdZ8LKiJBhQ)

---

## Ejercicio 1 — Experimenta con tokens

Abre [platform.openai.com/tokenizer](https://platform.openai.com/tokenizer) y prueba:

> 1. Escribe tu nombre completo. ¿Cuántos tokens tiene?
> 2. Escribe esta frase: *"La inteligencia artificial aprende de los datos"*. ¿Cuántos tokens?
> 3. Prueba con emojis. ¿Cuántos tokens consume un emoji?

Comparte el resultado más sorprendente con el grupo.

<details>
<summary>Pistas si te atascas</summary>

- Los nombres propios y palabras largas suelen "costar" más tokens que palabras cortas
- Los emojis consumen bastantes tokens a pesar de ser un solo carácter
- En inglés las palabras suelen tokenizarse de forma más eficiente que en español

</details>

---

## Las versiones de ChatGPT

No todos los ChatGPT son iguales. Estas son las versiones que encontrarás:

| Versión | Cuándo usarla |
|---|---|
| **GPT-4o** | El más equilibrado. Rápido y capaz. Para uso general. |
| **GPT-4o mini** | Más rápido y barato. Para tareas simples. |
| **o1 / o3** | Razonamiento profundo. Para problemas complejos, matemáticas, código. Va más lento. |

En el plan gratuito tienes acceso limitado a GPT-4o. En el de pago (Plus) tienes acceso completo a todos los modelos.

---

## La interfaz de ChatGPT

### El chat principal

Es donde escribes y recibes respuestas. Cada conversación es independiente y queda guardada en el historial de la izquierda.


### Proyectos

Los proyectos te permiten agrupar conversaciones bajo un mismo contexto. Puedes darle instrucciones permanentes al modelo para ese proyecto (por ejemplo: *"siempre responde en un tono informal"* o *"este proyecto es sobre mi negocio de fotografía"*).


### Memoria

ChatGPT puede recordar cosas sobre ti entre conversaciones. Si está activada, el modelo aprende tus preferencias con el tiempo.

Para activarla: **Perfil → Configuración → Personalización → Memoria**.

### Canvas

Un espacio de edición colaborativa donde puedes trabajar con el modelo en un documento o código de forma más visual, sin que las respuestas desaparezcan en el chat.

Muy útil para redactar textos largos o revisar documentos.

---

## Ejercicio 2 — Configura tu espacio

Haz esto ahora mismo en ChatGPT:

> 1. Crea un nuevo **Proyecto** y llámalo con tu nombre + "Curso IA"
> 2. En las instrucciones del proyecto escribe 3 cosas sobre ti que quieras que ChatGPT recuerde (tu profesión, tu tono preferido, para qué usarás la herramienta)
> 3. Activa la **Memoria** si no está activada
> 4. Entra en **Canvas** y pídele a ChatGPT que escriba una presentación tuya de 3 líneas


---

## Ejercicio 3 — Temperatura en la práctica

Sin tocar ningún ajuste técnico, prueba esto en el chat:

Escribe el mismo prompt de dos formas distintas y compara los resultados:

**Versión A (temperatura baja implícita):**
> *"Dame 5 nombres para una app de productividad. Sé directo y conciso."*

**Versión B (temperatura alta implícita):**
> *"Dame 5 nombres creativos y originales para una app de productividad. Sorpréndeme."*

<details>
<summary>Qué observar</summary>

- ¿Son los nombres de la versión A más genéricos?
- ¿Los de la versión B son más arriesgados o extraños?
- ¿Cuál te resulta más útil?

Esta es la esencia de cómo el prompt influye en el estilo de respuesta.

</details>

---

## Trabajo en equipo — Battle de temperaturas

*(30 minutos)*

### El reto

Todos los equipos reciben el mismo prompt de partida:

> *"Escribe una descripción de un producto para una tienda online."*

Cada equipo lo lanza de una forma diferente:

| Equipo | Instrucción añadida |
|---|---|
| **Opción 1** | *"Sé extremadamente preciso y técnico. Solo hechos."* |
| **Opción 2** | *"Sé creativo, sorprendente y usa metáforas inesperadas."* |
| **Opción 3** | *"Tono formal, corporativo, para una empresa del IBEX 35."* |
| **Opción 4** | *"Tono cercano, como si se lo explicaras a un amigo por WhatsApp."* |



### Puesta en común

Cada equipo lee su resultado en voz alta. Debatid:
- ¿Cuál os parece más efectivo para vender?
- ¿Qué ha cambiado entre los resultados siendo el mismo producto?
- ¿Qué conclusión sacáis sobre cómo el prompt controla el tono?

---

## Lo que aprendiste hoy

- Un LLM predice la siguiente palabra — de ahí surge todo lo que parece inteligencia
- ChatGPT lee tokens, no palabras, y tiene un límite de contexto por conversación
- La temperatura controla creatividad vs. precisión, y puedes influirla desde el prompt
- GPT-4o es la versión más equilibrada para uso general
- Los proyectos y la memoria te permiten personalizar ChatGPT para tu caso concreto

---

*Mañana: las limitaciones de la IA — alucinaciones, sesgos y cómo usarla con criterio.*
