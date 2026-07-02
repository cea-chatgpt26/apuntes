# Día 3 — Limitaciones de la IA y tu Primer Prompt

**Módulo 1 · Fundamentos de IA y ChatGPT**

---

## Recapitulando el día anterior

En una frase:

> **¿Qué es un token y por qué importa?**

---

## Las limitaciones que debes conocer

Usar ChatGPT sin conocer sus límites es como conducir sin saber que el coche tiene puntos ciegos. Hoy los vemos todos.

---

### 1. Las alucinaciones

La limitación más importante y menos conocida.

ChatGPT a veces **inventa información con total confianza**. No lo hace con mala intención — es una consecuencia de cómo funciona. El modelo predice la respuesta más plausible, y a veces esa respuesta simplemente no es verdad.

Puede inventarse:
- Estadísticas y estudios científicos que no existen
- Citas de personas reales que nunca dijeron eso
- Leyes, artículos o normativas incorrectas
- Bibliografía con títulos y autores falsos
- Eventos históricos con fechas erróneas

**La regla de oro:** nunca uses un dato importante de ChatGPT sin verificarlo en otra fuente.

---

### 2. El corte de conocimiento

ChatGPT fue entrenado hasta una fecha concreta. **No sabe lo que pasó después.**

Si le preguntas por noticias recientes, resultados deportivos de esta semana o el último modelo de iPhone, puede darte información desactualizada o simplemente decirte que no sabe.

Cada modelo tiene su fecha de corte. GPT-4o tiene conocimiento hasta principios de 2024 aproximadamente.

> **Solución:** para información actual, usa Perplexity (lo veremos en el Día 13) o activa la búsqueda web en ChatGPT si tienes acceso.

---

### 3. No tiene acceso a internet por defecto

A menos que uses plugins o herramientas específicas, ChatGPT trabaja solo con lo que aprendió durante el entrenamiento. No puede visitar páginas web, leer PDFs externos ni consultar bases de datos en tiempo real.

---

### 4. No te conoce (a menos que se lo cuentes)

ChatGPT no sabe quién eres, a qué te dedicas, ni qué necesitas. Cada conversación empieza desde cero a menos que uses proyectos o memoria (lo configuraste ayer).

Por eso el contexto en el prompt es tan importante — lo veremos ahora mismo.

---

### 5. Los sesgos

El modelo fue entrenado con texto escrito por humanos. Y los humanos tenemos sesgos. El resultado es que ChatGPT puede:

- Sobrerrepresentar perspectivas occidentales o anglófonas
- Dar respuestas más conservadoras en temas delicados
- Reflejar estereotipos presentes en los datos de entrenamiento

No es un árbitro neutral. Es un reflejo estadístico de mucho texto humano.

---

## Ejercicio 1 — Caza una alucinación

Prueba estos prompts en ChatGPT y verifica las respuestas:

> 1. *"Dame 3 estudios científicos recientes sobre los beneficios de la meditación con sus autores y año de publicación"*
> 2. *"¿Qué dijo [persona famosa de tu sector] sobre la inteligencia artificial?"*

Busca en Google si esos estudios o citas existen realmente.

<details>
<summary>Qué suele pasar</summary>

- Los estudios pueden tener títulos verosímiles pero autores o revistas inventadas
- Las citas de personas famosas suelen sonar auténticas pero ser fabricadas
- Si preguntas a ChatGPT si está seguro, a menudo dice que sí — incluso cuando se ha equivocado

Esto no significa que ChatGPT sea inútil. Significa que hay que usarlo con criterio.

</details>

---

## ¿Qué es un prompt?

Un **prompt** es el mensaje que le escribes a ChatGPT. Todo lo que obtienes depende de cómo lo escribas.

La mayoría de la gente usa ChatGPT como un buscador: escribe una pregunta corta y espera una respuesta. Eso está muy lejos de su potencial real.

Un prompt bien construido puede transformar completamente la calidad de la respuesta.

---

## La estructura de un buen prompt

Todo prompt efectivo tiene hasta cinco elementos. No siempre necesitas los cinco, pero conocerlos te da control total.

### 1. Rol
*¿Quién quieres que sea ChatGPT?*

> *"Actúa como un experto en marketing digital con 10 años de experiencia..."*
> *"Eres un profesor de primaria explicando conceptos a niños de 8 años..."*

Asignar un rol ajusta el tono, el vocabulario y el enfoque de la respuesta.

### 2. Contexto
*¿Qué información necesita saber antes de responder?*

> *"Tengo un negocio de fotografía de bodas con 3 años de experiencia. Mi cliente ideal son parejas de entre 28 y 40 años..."*

Sin contexto, ChatGPT hace suposiciones. Con contexto, personaliza.

### 3. Tarea
*¿Qué quieres exactamente que haga?*

> *"Escribe...", "Resume...", "Analiza...", "Dame una lista de...", "Corrige..."*

Sé específico. "Ayúdame con mi web" es vago. "Escribe 3 versiones del titular de mi página de inicio" es accionable.

### 4. Formato
*¿Cómo quieres que te entregue el resultado?*

> *"...en forma de tabla", "...en menos de 100 palabras", "...con viñetas", "...como si fuera un email profesional"*

### 5. Restricciones
*¿Qué quieres que evite?*

> *"...sin usar tecnicismos", "...sin mencionar a la competencia", "...sin emojis"*

---

## Ejercicio 2 — Del prompt malo al prompt bueno

Reescribe estos prompts aplicando la estructura que acabas de aprender:

**Prompt malo 1:**
> *"Ayúdame con mis redes sociales"*

**Prompt malo 2:**
> *"Explícame el marketing"*

**Prompt malo 3:**
> *"Escribe algo para mi negocio"*

<details>
<summary>Ejemplo de cómo mejorar el primero</summary>

**Prompt mejorado:**
> *"Actúa como un community manager especializado en pequeños negocios locales. Tengo una panadería artesanal en Madrid con presencia en Instagram (2.000 seguidores). Dame 5 ideas de publicaciones para esta semana que aumenten la interacción, con el texto listo para publicar. Tono cercano y sin emojis."*

Fíjate en los cinco elementos:
- **Rol:** community manager especializado en negocios locales
- **Contexto:** panadería artesanal en Madrid, 2.000 seguidores en Instagram
- **Tarea:** 5 ideas de publicaciones con texto listo
- **Formato:** texto listo para publicar
- **Restricción:** tono cercano, sin emojis

</details>

---

## Ejercicio 3 — Compara en vivo

Abre ChatGPT y prueba los dos extremos:

**Primero escribe:**
> *"Escríbeme un email para un cliente"*

**Luego escribe una versión con los 5 elementos** (adapta a tu sector).

Compara los resultados. La diferencia debería ser notable.

---

## Trabajo en equipo — Caza de alucinaciones

*(30 minutos)*

### El reto

Cada equipo elige un tema relacionado con su sector o intereses y pide a ChatGPT datos concretos y verificables:

> *"Dame 3 estudios científicos sobre [tema] con autor, año y revista donde se publicaron."*
>
> *"¿Qué dijo [experto conocido de vuestro sector] sobre [tema concreto]?"*
>
> *"Dame las 5 leyes o normativas más importantes sobre [tema] en España con su número y fecha de aprobación."*

Después verificad cada dato en Google. Apuntad cuántos son reales y cuántos inventados.

### Competición

El equipo que encuentre la alucinación **más elaborada y convincente** gana. Presentadla al grupo: qué preguntasteis, qué respondió ChatGPT y qué encontrasteis al verificarlo.

### Reflexión final

- ¿En qué temas alucina más?
- ¿Cómo escribirías el prompt para reducir las alucinaciones?
- ¿En qué situaciones de vuestro trabajo esto podría ser un problema real?

---

## Lo que aprendiste hoy

- ChatGPT alucina: verifica siempre los datos importantes en otra fuente
- Tiene un corte de conocimiento y no accede a internet por defecto
- Los sesgos del modelo vienen de los datos con los que fue entrenado
- Un prompt tiene cinco elementos: rol, contexto, tarea, formato y restricciones
- La diferencia entre un prompt vago y uno estructurado es la diferencia entre una respuesta genérica y una útil

---

*Mañana: Prompt Engineering avanzado — few-shot prompting y cómo enseñarle a ChatGPT con ejemplos.*
