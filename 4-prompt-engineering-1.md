# Día 4 — Prompt Engineering I: Few-Shot Prompting

**Módulo 2 · Desafíos y Avances en Inteligencia Artificial**

---

## Recapitulando el día anterior

Rápido:

> **Nombra los 5 elementos de un prompt bien estructurado.**

Si los recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 3 antes de continuar.

---

## De los prompts básicos a los avanzados

Ayer aprendiste a estructurar un prompt con rol, contexto, tarea, formato y restricciones. Eso ya te pone por delante del 80% de los usuarios de ChatGPT.

Hoy vas un paso más allá: aprenderás a **enseñarle con ejemplos** — una de las técnicas más potentes del prompt engineering.

---

## Zero-shot, One-shot y Few-shot

Estas tres técnicas se diferencian por la cantidad de ejemplos que incluyes en el prompt.

### Zero-shot
Le pides algo sin dar ningún ejemplo. ChatGPT hace lo que puede con su conocimiento general.

> *"Clasifica este email como urgente o no urgente: 'Hola, necesito el informe para mañana.'"*

Funciona bien para tareas simples y genéricas.

### One-shot
Le das un ejemplo antes de pedirle que haga la tarea.

> *"Clasifica emails como urgente o no urgente.
> Ejemplo: 'Hola, ¿quedamos el viernes?' → No urgente
> Ahora clasifica este: 'Necesito el informe para mañana.'"*

El modelo entiende mejor el criterio porque ha visto un caso real.

### Few-shot
Le das dos o más ejemplos. El modelo calibra su respuesta basándose en el patrón que le muestras.

> *"Clasifica emails como urgente o no urgente.
> 'Hola, ¿quedamos el viernes?' → No urgente
> 'El servidor está caído, clientes sin acceso.' → Urgente
> 'Necesito el informe para el jueves o el lunes.' → No urgente
> Ahora clasifica: 'El cliente lleva 3 días esperando respuesta.'"*

**¿Por qué funciona?** Porque le estás mostrando tu criterio real, no el genérico del modelo. Es la diferencia entre "lo que ChatGPT cree que quieres" y "exactamente lo que quieres".

---

## ¿Cuándo usar cada técnica?

| Situación | Técnica recomendada |
|---|---|
| Tarea simple o genérica | Zero-shot |
| Quieres un estilo o tono específico | Few-shot |
| El modelo no entiende lo que pides en zero-shot | One-shot o Few-shot |
| Necesitas consistencia en múltiples outputs | Few-shot |
| Tarea muy especializada o con criterio propio | Few-shot con 3-5 ejemplos |

---

## Ejercicio 1 — Compara los tres

Prueba los tres niveles con la misma tarea. Copia y pega cada uno en ChatGPT:

**Zero-shot:**
> *"Escribe el asunto de este email de forma más atractiva: 'Reunión de seguimiento del proyecto'"*

**One-shot:**
> *"Mejora el asunto de emails para que sean más atractivos.
> Original: 'Envío de factura' → Mejorado: 'Tu factura de octubre está lista'
> Ahora mejora: 'Reunión de seguimiento del proyecto'"*

**Few-shot:**
> *"Mejora el asunto de emails para que sean más atractivos y directos.
> Original: 'Envío de factura' → Mejorado: 'Tu factura de octubre está lista'
> Original: 'Actualización del estado' → Mejorado: '3 cosas que han cambiado esta semana'
> Original: 'Recordatorio' → Mejorado: 'Te esperamos mañana a las 10h'
> Ahora mejora: 'Reunión de seguimiento del proyecto'"*

<details>
<summary>Qué observar en los resultados</summary>

- El resultado zero-shot suele ser correcto pero genérico
- El one-shot ya empieza a captar el patrón (más directo, más concreto)
- El few-shot debería darte el resultado más cercano al estilo que muestran los ejemplos
- Si los tres resultados son similares, prueba con una tarea más específica o especializada — ahí es donde few-shot marca más diferencia

</details>

---

## Cómo construir buenos ejemplos

No todos los ejemplos son útiles. Estos son los criterios para que funcionen:

**Variedad:** los ejemplos deben cubrir distintos casos, no el mismo caso repetido con otras palabras.

**Claridad:** el patrón entrada → salida tiene que ser obvio. Si tus ejemplos son ambiguos, el modelo se confunde.

**Representatividad:** elige ejemplos que representen bien lo que quieres. Si todos tus ejemplos son casos fáciles, el modelo fallará en los difíciles.

**Cantidad:** entre 2 y 5 ejemplos suele ser suficiente. Más de 5 raramente mejora el resultado y consume más tokens.

---

## Few-shot para estilos y tonos

Una de las aplicaciones más potentes: enseñarle tu propio estilo de escritura.

```xml
<prompt>
  <rol>Eres un asistente de escritura que replica mi estilo exacto.</rol>

  <ejemplos>
    <ejemplo>
      <entrada>Post sobre productividad</entrada>
      <salida>La agenda perfecta no existe. Existe la agenda que cumples.
      Eso es todo.</salida>
    </ejemplo>
    <ejemplo>
      <entrada>Post sobre aprender cosas nuevas</entrada>
      <salida>Llevas 6 meses queriendo aprender diseño.
      En ese tiempo podrías haber completado un curso entero.
      El problema no es el tiempo. Es la decisión.</salida>
    </ejemplo>
  </ejemplos>

  <tarea>
    Escribe un post sobre el miedo a empezar un negocio.
    Replica exactamente el estilo de los ejemplos: frases cortas, tono directo,
    sin rodeos, un golpe de realidad al final.
  </tarea>

  <restricciones>
    <evitar>Frases motivacionales vacías</evitar>
    <evitar>Más de 4 líneas en total</evitar>
  </restricciones>
</prompt>
```

Con este prompt, ChatGPT no escribe como ChatGPT — escribe como tú.

---

## Ejercicio 2 — Clona tu estilo

Elige 2 textos que hayas escrito tú (emails, posts, mensajes profesionales) y constrúyelos como ejemplos few-shot.

Luego pídele a ChatGPT que escriba algo nuevo en ese mismo estilo.

> *Consejo:* cuanto más distintos sean los dos ejemplos entre sí, mejor calibra el modelo tu estilo general.

<details>
<summary>Si no tienes textos propios</summary>

Usa textos de alguien cuyo estilo admires: un autor, un comunicador, una marca.

El proceso es el mismo: copias fragmentos como ejemplos y pides al modelo que replique ese tono.

</details>

---

## Ejercicio 3 — Few-shot para tu sector

Piensa en una tarea repetitiva de tu trabajo que implique escribir (emails, informes, descripciones, respuestas a clientes...).

Construye un prompt few-shot con 3 ejemplos reales de esa tarea. Lánzalo y compara el resultado con lo que obtendrías sin ejemplos.

---

## Trabajo en equipo — El prompt perfecto

*(30 minutos)*

### El reto

Todos los equipos tienen el mismo objetivo: conseguir el mejor asunto posible para un email de ventas dirigido a pequeñas empresas anunciando un nuevo software de gestión.

Cada equipo usa una técnica diferente:

| Equipo | Técnica |
|---|---|
| **Equipo 1** | Zero-shot — sin ejemplos, solo la petición |
| **Equipo 2** | One-shot — un ejemplo de buen asunto antes de la petición |
| **Equipo 3** | Few-shot — tres ejemplos de asuntos que han funcionado bien |
| **Equipo 4** | Prompt completo con los 5 elementos + few-shot |

### Votación

Cada equipo presenta su mejor resultado. El grupo vota cuál es el asunto más efectivo (sin saber qué técnica usó cada equipo).

Luego reveláis las técnicas y debatid:
- ¿Ha ganado el más elaborado o el más simple?
- ¿Qué añadir o quitar habría mejorado el resultado?
- ¿En qué situaciones de vuestro trabajo usaríais cada técnica?

---

## Lo que aprendiste hoy

- Zero-shot: sin ejemplos. One-shot: un ejemplo. Few-shot: varios ejemplos.
- Few-shot calibra el criterio del modelo con tu estándar real, no con el genérico
- Los buenos ejemplos son variados, claros y representativos
- Puedes usar few-shot para enseñarle tu propio estilo de escritura
- Entre 2 y 5 ejemplos es suficiente en la mayoría de casos

---

*Mañana: Chain-of-Thought — cómo hacer que ChatGPT razone paso a paso antes de responder.*
