# Día 6 — Prompts por objetivo y sector

**Módulo 2 · Desafíos y Avances en Inteligencia Artificial**

---

## Recapitulando el día anterior

> **¿Qué es el Chain-of-Thought y qué diferencia produce en la respuesta?**

---

## Las mismas técnicas, un uso distinto según para qué las uses

Ya conoces las piezas: estructura de 5 elementos, few-shot, chain-of-thought, iteración. Con esto puedes construir cualquier prompt.

Pero hay una pregunta que todavía no te has hecho: **¿para qué quiero exactamente esta respuesta, y quién la va a usar?**

Un mismo prompt mal orientado da resultados mediocres aunque esté técnicamente bien construido. Hoy aprendes a afinar la puntería: primero por **objetivo**, luego por **sector**.

---

## Los 6 objetivos más habituales

Antes de escribir un prompt, identifica qué quieres conseguir. No es lo mismo pedir que informar que pedir que convenza.

### 1. Informar / explicar
Quieres que el modelo transmita conocimiento con claridad.

> *"Explícame cómo funciona el interés compuesto como si tuviera 15 años, con un ejemplo numérico."*

### 2. Persuadir / vender
Quieres generar una acción o cambio de opinión en quien lo lea.

> *"Escribe un email persuasivo para que un cliente que canceló hace 3 meses vuelva a contratar el servicio, sin sonar desesperado."*

### 3. Resumir / sintetizar
Quieres reducir información sin perder lo esencial.

> *"Resume este informe de 10 páginas en 5 bullets, priorizando cifras y decisiones, no contexto."*

### 4. Generar ideas / brainstorming
Quieres cantidad y variedad, no una respuesta única y perfecta.

> *"Dame 15 ideas de nombres para una app de gestión de tareas para autónomos. No filtres, incluye ideas arriesgadas."*

### 5. Resolver un problema / analizar
Quieres que el modelo razone sobre una situación concreta y llegue a una conclusión.

> *"Analiza por qué las ventas de la tienda online bajaron un 20% en marzo, dadas estas variables: [datos]. Da 3 hipótesis ordenadas por probabilidad."*

### 6. Crear contenido
Quieres un texto (o guion, o estructura) listo para usar.

> *"Escribe el guion de un vídeo de 60 segundos presentando nuestro nuevo producto a pymes del sector hostelero."*

**El primer paso de cualquier prompt bueno no es escribirlo — es decidir a cuál de estos 6 pertenece.** Eso determina el tono, la longitud y si necesitas ejemplos o razonamiento paso a paso.

---

## El mismo objetivo, sectores distintos

Aquí está la parte que casi nadie hace: **adaptar el prompt al sector**, no solo al objetivo.

"Persuadir" no se escribe igual en marketing que en un contexto legal. "Resumir" no se escribe igual para un médico que para un profesor.

| Sector | Vocabulario y tono | Restricciones típicas |
|---|---|---|
| **Marketing / ventas** | Cercano, orientado a beneficio, emocional | Evitar sonar a publicidad genérica |
| **Salud** | Preciso, empático, nunca diagnóstico | Nunca sustituir consejo médico profesional |
| **Legal** | Formal, exacto, sin ambigüedad | Aclarar que no sustituye asesoría legal real |
| **Educación** | Claro, progresivo, con ejemplos | Adaptar al nivel del alumno, sin dar por sabido |
| **Hostelería / retail** | Cálido, práctico, orientado a experiencia | Evitar tecnicismos, ir al grano |
| **RRHH** | Neutral, respetuoso, orientado a proceso | Cuidado con sesgos en selección o evaluación |

Fíjate que la tabla no cambia el **objetivo** (informar, persuadir, resumir...) — cambia **cómo se ejecuta** ese objetivo.

---

## La plantilla objetivo + sector

Combinando lo que ya sabías (rol, contexto, tarea, formato, restricciones) con el objetivo y el sector, el prompt queda así:

```xml
<prompt>
  <rol>Eres [rol específico del sector].</rol>

  <objetivo>[Informar / Persuadir / Resumir / Generar ideas / Resolver un problema / Crear contenido]</objetivo>

  <contexto>[Datos concretos del negocio, situación o audiencia]</contexto>

  <tarea>[Qué quieres exactamente]</tarea>

  <tono>[Cómo debe sonar, propio del sector]</tono>

  <restricciones>
    <evitar>[Lo que no debe hacer, propio del sector]</evitar>
  </restricciones>
</prompt>
```

No necesitas escribirlo siempre en XML, pero pensar en estos seis bloques antes de escribir el prompt evita el 90% de las respuestas genéricas.

---

## Ejercicio 1 — Identifica el objetivo

Para cada situación, di cuál de los 6 objetivos es el correcto antes de escribir ningún prompt:

1. Necesitas que un cliente enfadado por un retraso en la entrega se quede tranquilo y no pida el reembolso.
2. Tienes 40 páginas de una normativa nueva y necesitas quedarte con lo que afecta a tu departamento.
3. Tu equipo lleva dos semanas sin ideas para la campaña de Navidad.

<details>
<summary>Respuesta</summary>

1. **Persuadir** (aunque también hay un componente de gestión emocional)
2. **Resumir**
3. **Generar ideas**

Si identificas mal el objetivo, el prompt que escribas —por bien construido que esté— apuntará al sitio equivocado.

</details>

---

## Ejercicio 2 — Un objetivo, tres sectores

Coge el objetivo **"informar"** y escribe tres prompts distintos para explicar el mismo concepto —por ejemplo, "qué es la inteligencia artificial"— adaptado a:

1. Un cliente de una tienda de electrónica (sector retail)
2. Un alumno de secundaria (sector educación)
3. El comité directivo de una empresa que evalúa invertir en IA (sector empresarial)

Compara los tres resultados: mismo objetivo, mismo tema, tono y profundidad completamente distintos.

<details>
<summary>Qué deberías observar</summary>

- El de retail debería ser breve, práctico, con ejemplos de producto
- El de educación debería tener analogías simples y evitar jerga técnica
- El del comité directivo debería centrarse en implicaciones de negocio, riesgos y ROI, no en cómo funciona técnicamente

Si los tres textos se parecen demasiado, el prompt no estaba realmente adaptado al sector — solo cambiaste una palabra.

</details>

---

## Ejercicio 3 — Tu propio sector

Piensa en tu trabajo o el de alguien de tu equipo. Elige uno de los 6 objetivos y escribe un prompt completo usando la plantilla `<rol> <objetivo> <contexto> <tarea> <tono> <restricciones>`.

Pruébalo en ChatGPT. Si el resultado no encaja con tu sector, revisa qué bloque de la plantilla estaba flojo o vacío.

---

## Trabajo en equipo — Prompts a medida

*(30 minutos)*

### El reto

Cada equipo recibe al azar:
- **Una tarjeta de sector**: marketing, salud, legal, educación, hostelería o RRHH
- **Una tarjeta de objetivo**: informar, persuadir, resumir, generar ideas, resolver un problema o crear contenido

Con esa combinación, el equipo tiene 15 minutos para construir el mejor prompt posible usando la plantilla de hoy, lanzarlo a ChatGPT y quedarse con el mejor resultado.

### Presentación a ciegas

Cada equipo lee en voz alta **solo la respuesta de ChatGPT**, sin decir qué sector ni qué objetivo le tocó. El resto del grupo intenta adivinar ambos.

### Puesta en común

- ¿Se notaba claramente el sector en el resultado, o sonaba genérico?
- ¿Qué parte de la plantilla marcó más la diferencia: el tono, las restricciones o el contexto?
- ¿Qué cambiaríais del prompt si tuvierais que repetirlo?

---

## Lo que aprendiste hoy

- Antes de escribir un prompt, identifica su objetivo: informar, persuadir, resumir, generar ideas, resolver un problema o crear contenido
- El mismo objetivo se ejecuta de forma distinta según el sector: cambia el tono, el vocabulario y las restricciones
- Combinar objetivo + sector + los 5 elementos de un buen prompt reduce casi por completo las respuestas genéricas
- La plantilla `<rol> <objetivo> <contexto> <tarea> <tono> <restricciones>` te sirve como checklist rápido
- Si dos prompts para sectores distintos suenan igual, algo en la adaptación falló

---

*Mañana: IA generativa de imágenes — cómo funcionan DALL·E, Midjourney y Stable Diffusion.*
