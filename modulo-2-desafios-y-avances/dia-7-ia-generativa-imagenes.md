# Día 7 — IA generativa: imágenes

**Módulo 2 · Desafíos y Avances en Inteligencia Artificial**

---

## Recapitulando el día anterior

Rápido:

> **¿Qué diferencia hay entre adaptar un prompt por objetivo y adaptarlo por sector?**

Si lo recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 6 antes de continuar.

---

## De los prompts de texto a los prompts de imagen

Todo lo que aprendiste en los días 4, 5 y 6 —rol, contexto, ejemplos, iteración— también aplica a la generación de imágenes. La diferencia es que ahora el "rol" y el "formato" del prompt se traducen en cosas visuales: estilo, encuadre, luz, cámara.

Hoy vas a aprender dos cosas: **cómo estructurar un buen prompt de imagen** (que sirve para cualquier herramienta) y **qué herramienta usar según lo que necesites**, todas gratuitas o con plan gratuito suficiente para practicar.

---

## La estructura de un buen prompt de imagen

Antes de mirar herramientas concretas, necesitas una plantilla mental. Un prompt de imagen flojo dice *"un perro en un parque"*. Un prompt bien estructurado controla seis elementos:

| Elemento | Qué define | Ejemplo |
|---|---|---|
| **Sujeto** | Qué o quién aparece, y qué está haciendo | "Un golden retriever corriendo" |
| **Estilo/medio** | Técnica visual: foto, ilustración, 3D, acuarela... | "fotografía realista" |
| **Composición** | Encuadre, plano, ángulo | "plano medio, cámara a la altura del suelo" |
| **Luz y color** | Iluminación, paleta, ambiente | "luz dorada de atardecer, tonos cálidos" |
| **Detalles técnicos** | Cámara, lente, render engine, nivel de detalle | "lente 85mm, profundidad de campo baja, alta resolución" |
| **Negativos** | Qué NO quieres que aparezca | "sin texto, sin personas de fondo" |

Con estos seis elementos, tu prompt queda así:

> *"Fotografía realista de un golden retriever corriendo en un parque al atardecer, plano medio a la altura del suelo, luz dorada cálida, lente 85mm con fondo desenfocado, alta resolución. Sin texto ni personas en la imagen."*

Comparado con *"un perro en un parque"*, este prompt le da al modelo un criterio real en vez de dejarlo improvisar — exactamente la misma lógica que el few-shot del día 4: cuanto más específico seas, menos rellena el modelo con lo genérico.

**No necesitas usar los seis elementos siempre.** Para bocetos rápidos, con sujeto + estilo suele bastar. Para piezas finales (marketing, portadas, producto), cuantos más elementos controles, menos regeneraciones necesitarás.

### El mismo prompt en formato XML

Igual que con los prompts de texto, escribir la petición como bloques etiquetados ayuda al modelo a distinguir cada elemento y evita que se te olvide alguno:

```xml
<prompt>
  <sujeto>Un golden retriever corriendo, orejas al viento, mirada al frente</sujeto>

  <estilo>Fotografía realista, no ilustración ni 3D</estilo>

  <composicion>
    <plano>Medio</plano>
    <angulo>Cámara a la altura del suelo, ligeramente por debajo del perro</angulo>
  </composicion>

  <iluminacion>
    <momento>Atardecer</momento>
    <tono>Luz dorada y cálida</tono>
  </iluminacion>

  <detalles_tecnicos>
    <lente>85mm</lente>
    <profundidad_de_campo>Baja, fondo desenfocado</profundidad_de_campo>
    <resolucion>Alta, nivel de detalle en el pelaje</resolucion>
  </detalles_tecnicos>

  <negativos>
    <evitar>Texto o marcas de agua en la imagen</evitar>
    <evitar>Personas u otros animales de fondo</evitar>
  </negativos>
</prompt>
```

Este formato es opcional — funciona igual de bien escrito en una sola frase como en el ejemplo anterior. La ventaja del XML aparece cuando el prompt crece: con muchos elementos, las etiquetas evitan que el modelo mezcle o ignore alguno, igual que viste con los prompts de texto del día 4.

---

## Iterar sobre una imagen

Igual que con texto, la primera imagen casi nunca es la definitiva. Las técnicas de iteración funcionan igual:

- **Pide cambios puntuales**: *"mantén la composición pero cambia la luz a un día nublado"*
- **Da referencias**: sube una imagen de referencia de estilo o de producto si la herramienta lo permite
- **Ajusta un elemento a la vez**: cambiar estilo y composición a la vez dificulta saber qué mejoró o empeoró el resultado

---

## Las herramientas: dónde generar imágenes gratis

Estas son las principales IAs de imagen con plan gratuito real (no solo prueba de unos días):

| Herramienta | Motor | Gratis | Mejor para |
|---|---|---|---|
| **ChatGPT** (GPT Image) | Modelo de OpenAI integrado en ChatGPT | Sí, con límite de generaciones/día en el plan free | Iterar con conversación: "cambia esto", "prueba otro estilo" |
| **Gemini** (Imagen / "Nano Banana") | Modelo de Google integrado en Gemini | Sí, con límite diario | Edición de imágenes existentes y coherencia con el resto del ecosistema Google |
| **Ideogram** | Modelo propio, especializado en texto dentro de imagen | Sí, plan free con créditos diarios | Imágenes con texto legible: logos, carteles, memes, portadas con títulos |
| **Copilot Designer / Bing Image Creator** | DALL·E 3 (Microsoft) | Sí, gratis con cuenta Microsoft | Alternativa gratuita e ilimitada-ish a DALL·E 3 sin pagar ChatGPT Plus |
| **Leonardo.Ai** | Varios modelos (Phoenix, Flux...) | Sí, créditos diarios gratis | Control fino: modelos por estilo, "canvas" de edición, consistencia de personajes |
| **Adobe Firefly** | Modelo propio Adobe | Sí, créditos mensuales gratis | Uso comercial seguro (entrenado con contenido con licencia) e integración con Photoshop |
| **Playground AI** | Varios modelos (Flux, SDXL...) | Sí, generaciones diarias gratis | Probar varios modelos y estilos rápido, comunidad de prompts públicos |

**Nota sobre Midjourney:** sigue siendo referencia de calidad artística, pero ya no tiene plan gratuito — solo suscripción. Por eso no está en esta lista, aunque la mencionaremos como referencia de estilo.

---


## Ejercicio 1 — Construye tu prompt con la plantilla

Elige un sujeto simple (un producto, un animal, un lugar) y escribe un prompt usando los seis elementos de la plantilla: sujeto, estilo, composición, luz, detalles técnicos y negativos.

Pruébalo en **dos herramientas distintas** de la tabla (por ejemplo ChatGPT y Ideogram) y compara los resultados.

<details>
<summary>Qué observar en los resultados</summary>

- ¿Las dos herramientas interpretan igual el estilo pedido?
- ¿Alguna ignora algún elemento del prompt (por ejemplo la composición)?
- ¿Cuál se acerca más a lo que tenías en mente?

No hay una herramienta "mejor" en general — cada una interpreta el mismo prompt de forma distinta.

</details>

---

## Ejercicio 2 — Texto dentro de la imagen

La mayoría de modelos generan texto ilegible o deformado dentro de una imagen (letreros, logos, títulos). Prueba a pedir una imagen con texto legible en **Ideogram** y luego el mismo prompt en **ChatGPT** o **Gemini**.

> *"Cartel de una cafetería con el texto 'CAFÉ ABIERTO 24H' en letras grandes, estilo vintage, colores cálidos."*

<details>
<summary>Qué deberías ver</summary>

Ideogram está entrenado específicamente para renderizar texto legible — debería acertar el texto exacto con más frecuencia que el resto. Es la razón por la que muchos diseñadores lo usan para carteles, portadas o memes.

</details>

---

## Ejercicio 3 — Itera en 3 rondas

Genera una imagen, y sin cambiar el sujeto, pide dos cambios sucesivos (por ejemplo: primero cambia el estilo, luego cambia la luz). Comprueba si la herramienta mantiene la composición o la reinventa cada vez.

> *Consejo:* las herramientas conversacionales (ChatGPT, Gemini) suelen mantener mejor la coherencia entre iteraciones que las que generan desde cero cada vez.

---

## Trabajo en equipo — Duelo de imágenes

*(30 minutos)*

### El reto

Todos los equipos reciben el mismo brief: *"Imagen para la portada de un ebook sobre productividad, dirigido a emprendedores."*

Cada equipo construye su prompt usando la plantilla de 6 elementos, pero cada uno genera en una herramienta distinta:

| Equipo | Herramienta |
|---|---|
| **Equipo 1** | ChatGPT (GPT Image) |
| **Equipo 2** | Gemini |
| **Equipo 3** | Ideogram |
| **Equipo 4** | Leonardo.Ai o Playground AI |

### Votación

Cada equipo presenta su mejor resultado (máximo 3 intentos). El grupo vota cuál usaría de verdad como portada, sin saber qué herramienta usó cada equipo.

Debatid después:
- ¿Ganó la herramienta o el prompt?
- ¿Qué equipo tuvo que iterar más veces para llegar a un resultado usable?
- ¿En qué proyecto real de vuestro trabajo usaríais cada herramienta?

---

## Lo que aprendiste hoy

- Un buen prompt de imagen controla sujeto, estilo, composición, luz, detalles técnicos y negativos
- La misma lógica de iteración del prompt de texto aplica a imágenes: cambia un elemento a la vez
- ChatGPT y Gemini son las mejores para iterar de forma conversacional
- Ideogram es la referencia cuando necesitas texto legible dentro de la imagen
- Existen alternativas gratuitas de calidad (Copilot Designer, Leonardo.Ai, Firefly, Playground) que no requieren pagar suscripción
- Midjourney sigue siendo referencia de calidad artística, pero ya no ofrece plan gratuito

---

*Mañana: IA generativa de vídeo y audio — Sora, Runway, ElevenLabs y Suno.*
