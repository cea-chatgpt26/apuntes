# Día 5 — Prompt Engineering II: Chain-of-Thought e Iteración

**Módulo 2 · Desafíos y Avances en Inteligencia Artificial**

---

## Recapitulando el día anterior

> **¿Cuál es la diferencia entre zero-shot y few-shot? Pon un ejemplo de cuándo usarías cada uno.**

---

## El problema de las respuestas directas

Cuando le haces una pregunta compleja a ChatGPT sin más contexto, el modelo salta directamente a la respuesta. Y a veces esa respuesta es superficial, incorrecta o incompleta.

El motivo: igual que a un humano le cuesta resolver un problema difícil de cabeza sin escribir nada, al modelo también le cuesta "razonar" sin que le obligues a hacerlo paso a paso.

La solución se llama **Chain-of-Thought**.

---

## ¿Qué es el Chain-of-Thought?

**Chain-of-Thought** (cadena de pensamiento) es una técnica que obliga al modelo a razonar en voz alta antes de dar la respuesta final.

En lugar de preguntar directamente, le pides que muestre su proceso:

**Sin Chain-of-Thought:**
> *"¿Debería contratar a un diseñador o usar Canva para mi negocio?"*

**Con Chain-of-Thought:**
> *"¿Debería contratar a un diseñador o usar Canva para mi negocio? Antes de responder, analiza paso a paso los pros y contras de cada opción teniendo en cuenta que soy un autónomo con presupuesto limitado y necesito tener la web lista en 2 semanas."*

El segundo prompt genera una respuesta más profunda porque el modelo tiene que construir el razonamiento, no solo recuperarlo.

---

## Tres formas de activar el Chain-of-Thought

### 1. Instrucción directa
> *"Razona paso a paso antes de responder."*
> *"Piensa en voz alta."*
> *"Explica tu proceso de razonamiento."*

### 2. Estructura explícita
> *"Primero analiza el problema. Luego identifica las opciones. Finalmente recomienda la mejor."*

### 3. En XML
```xml
<razonamiento>
  Antes de responder, analiza el problema desde tres perspectivas:
  1. Qué gana el usuario
  2. Qué riesgos existen
  3. Qué alternativas hay
  Luego da tu recomendación final.
</razonamiento>
```

---

## Vídeo: Chain-of-Thought y Tree of Thought

Este vídeo explica CoT y va un paso más allá con el Tree of Thought — otra técnica avanzada que verás mencionada cada vez más:

[Prompts avanzados: Chain of Thought y Tree of Thought (≈12 min)](https://www.youtube.com/watch?v=OgsdcyDeQ2g)

---

## Ejercicio 1 — El mismo problema, dos respuestas

Prueba estos dos prompts y compara los resultados:

**Prompt A:**
> *"¿Es mejor hacer publicidad en Instagram o en Google para una pequeña empresa?"*

**Prompt B:**
> *"¿Es mejor hacer publicidad en Instagram o en Google para una pequeña empresa? Antes de responder, analiza paso a paso: qué tipo de audiencia llega a cada plataforma, en qué momento del proceso de compra están, cuánto suele costar cada opción y para qué tipo de negocio funciona mejor cada una. Luego da una recomendación clara."*

<details>
<summary>Qué observar</summary>

- El prompt A suele generar una respuesta genérica del tipo "depende de tu negocio"
- El prompt B fuerza al modelo a construir un argumento antes de concluir
- La recomendación final del B suele ser más accionable porque está respaldada por un razonamiento visible
- Puedes rebatir partes del razonamiento si no estás de acuerdo — eso es lo que lo hace útil

</details>

---

## La iteración: el superpoder más ignorado

La mayoría de usuarios escribe un prompt, lee la respuesta y si no es perfecta... escribe otro prompt desde cero.

Error. **La iteración dentro de la misma conversación es mucho más potente.**

ChatGPT recuerda todo lo que se ha dicho en el chat. Puedes construir encima de cada respuesta sin repetir el contexto.

### El ciclo de 3 rondas

```
Ronda 1 → Prompt inicial → Respuesta base
Ronda 2 → "Mejora X, añade Y, elimina Z" → Respuesta refinada
Ronda 3 → "Ahora hazlo más [concreto / breve / formal / creativo]" → Versión final
```

Cada ronda parte de donde dejó la anterior. En tres pasos puedes transformar una respuesta mediocre en exactamente lo que necesitabas.

---

## Ejercicio 2 — Las 3 rondas en acción

Sigue estas tres rondas sin cerrar la conversación:

**Ronda 1:**
> *"Escribe un párrafo de presentación para mi perfil de LinkedIn. Soy [tu profesión] con [X] años de experiencia en [sector]."*

**Ronda 2 (en el mismo chat):**
> *"Está bien pero suena demasiado genérico. Hazlo más específico, añade un logro concreto que haya tenido impacto y elimina los adjetivos vacíos como 'apasionado' o 'dinámico'."*

**Ronda 3 (en el mismo chat):**
> *"Ahora acórtalo a 3 frases máximo. Tiene que empezar con algo que llame la atención, no con mi nombre ni mi título."*

Compara la versión de la ronda 1 con la de la ronda 3. La diferencia suele ser notable.

<details>
<summary>Comandos útiles para la iteración</summary>

- *"Hazlo más breve / extenso"*
- *"Cambia el tono a [formal / informal / técnico / divulgativo]"*
- *"Añade un ejemplo concreto"*
- *"Elimina la parte de [X] y expande la de [Y]"*
- *"Reescríbelo en primera / tercera persona"*
- *"Dame 3 variaciones de la última respuesta"*
- *"Combina lo mejor de la versión 2 y la versión 3"*

</details>

---

## Ejercicio 3 — Documenta la evolución

Toma cualquier tarea de escritura real tuya (un email, una descripción, un informe) y aplica el ciclo de 3 rondas.

Al terminar, guarda las tres versiones una debajo de la otra. Verás visualmente cómo mejora en cada iteración.

Este ejercicio tiene doble objetivo: mejorar el resultado y entrenar el ojo para detectar qué pedir en cada ronda.

---

## Chain-of-Thought + Few-shot: la combinación más potente

Combinar ambas técnicas es el nivel más avanzado de prompt engineering para uso general.

```xml
<prompt>
  <rol>Eres un consultor de negocio con experiencia en pymes españolas.</rol>

  <ejemplos>
    <ejemplo>
      <problema>Una tienda de ropa quiere vender online pero no tiene presupuesto para web.</problema>
      <razonamiento>
        1. Opciones sin web propia: Instagram Shop, Wallapop, Vinted, marketplaces
        2. Coste: prácticamente cero en todas
        3. Audiencia: Instagram para ropa de marca, Vinted para segunda mano
        4. Velocidad: puede empezar hoy mismo
      </razonamiento>
      <recomendación>Empezar con Instagram Shop esta semana, sin inversión inicial.</recomendación>
    </ejemplo>
  </ejemplos>

  <razonamiento>
    Analiza el problema siguiendo el mismo esquema:
    1. Opciones disponibles
    2. Costes y recursos necesarios
    3. Audiencia objetivo
    4. Velocidad de implementación
  </razonamiento>

  <tarea>
    Un fisioterapeuta autónomo quiere conseguir más pacientes pero no sabe si
    centrarse en redes sociales, Google o el boca a boca. Dame una recomendación.
  </tarea>
</prompt>
```

---

## El prompt profesional: todo junto en XML

Aquí está el nivel más completo: un prompt que combina rol, contexto, few-shot con contraejemplo, chain-of-thought, formato y restricciones — todo dentro de una estructura XML.

Este tipo de prompt lo usarás cuando el resultado que necesitas sea muy específico y no puedas permitirte respuestas genéricas.

```xml
<prompt>

  <rol>
    Eres un community manager especializado en pequeños negocios de alimentación.
    Tu tono es cercano, auténtico y nunca suenas a publicidad.
  </rol>

  <contexto>
    Tengo una panadería artesanal en Madrid llamada "El Horno de Ana".
    Usamos masa madre, horneamos cada mañana y vendemos solo de martes a domingo.
    Nuestros clientes valoran la tradición y el producto local.
    Instagram: 2.100 seguidores. Mayor engagement los martes y jueves.
  </contexto>

  <ejemplos>
    <ejemplo tipo="bueno">
      <texto>El olor a pan recién horneado a las 7am no se puede describir. Solo se puede vivir. Te esperamos.</texto>
      <por-qué>Evoca sensación, no producto. Genera deseo sin mencionar precio.</por-qué>
    </ejemplo>
    <ejemplo tipo="malo">
      <texto>¡Ven a nuestra panadería! Tenemos el mejor pan de Madrid. ¡Síguenos!</texto>
      <por-qué>Genérico, autopromocional, no diferencia ni conecta emocionalmente.</por-qué>
    </ejemplo>
  </ejemplos>

  <razonamiento>
    Antes de escribir cada post, indica en una línea qué emoción o momento del día
    quieres activar en el lector. Luego escribe el post.
  </razonamiento>

  <tarea>
    Escribe 3 posts para Instagram para esta semana (martes, jueves y sábado).
    Cada uno debe parecer escrito por una persona real, no por una marca.
  </tarea>

  <formato>
    - Máximo 150 caracteres por post
    - Incluye el razonamiento previo en cursiva antes de cada post
    - Entrega los 3 posts listos para copiar y pegar
  </formato>

  <restricciones>
    <evitar>Emojis</evitar>
    <evitar>Mencionar precios o promociones</evitar>
    <evitar>Frases como "síguenos", "comparte" o "dale like"</evitar>
    <evitar>Adjetivos vacíos: "increíble", "delicioso", "espectacular"</evitar>
  </restricciones>

</prompt>
```

### ¿Qué técnicas usa este prompt?

| Técnica | Dónde aparece |
|---|---|
| **Rol** | `<rol>` — define quién es el modelo y cómo habla |
| **Few-shot** | `<ejemplos>` — un ejemplo bueno y uno malo para calibrar el estilo |
| **Contraejemplo** | `tipo="malo"` con explicación de por qué no funciona |
| **Chain-of-thought** | `<razonamiento>` — obliga al modelo a pensar antes de escribir |
| **Contexto rico** | `<contexto>` — datos específicos que evitan respuestas genéricas |
| **Formato estructurado** | `<formato>` — instrucciones precisas sobre el resultado |
| **Restricciones explícitas** | `<restricciones>` — lista clara de lo que debe evitar |

No necesitas usar XML siempre. Pero cuando un prompt es complejo o el resultado tiene que ser muy específico, esta estructura marca la diferencia.

---

## Trabajo en equipo — El prompt en 3 rondas

*(30 minutos)*

### El reto

Cada equipo recibe el mismo problema de partida:

> *"Una empresa de 5 personas quiere reducir el tiempo que dedica a reuniones internas."*

**Ronda 1:** Lanzad el problema a ChatGPT sin más contexto. Apuntad la respuesta.

**Ronda 2:** Refinad en el mismo chat pidiendo que razone paso a paso: qué causa las reuniones innecesarias, qué herramientas existen, qué cambio organizativo tendría más impacto rápido.

**Ronda 3:** Pedid que concrete en un plan de acción para la primera semana, con tareas específicas y responsables.

### Puesta en común

Cada equipo comparte su resultado final. Debatid:
- ¿Qué equipo obtuvo la respuesta más accionable?
- ¿Qué instrucciones de la ronda 2 o 3 marcaron más diferencia?
- ¿Qué aprendéis sobre cómo conversar con la IA en lugar de solo interrogarla?

---

## Lo que aprendiste hoy

- Chain-of-Thought obliga al modelo a razonar antes de responder — mejora la profundidad y precisión
- Puedes activarlo con una instrucción simple o con estructura XML
- La iteración en la misma conversación es más potente que empezar de cero cada vez
- El ciclo de 3 rondas transforma respuestas mediocres en resultados útiles
- Combinar few-shot + chain-of-thought es el nivel más alto del prompt engineering general

---

*Mañana: prompts por objetivo y sector — cómo adaptar ChatGPT a tu caso concreto.*
