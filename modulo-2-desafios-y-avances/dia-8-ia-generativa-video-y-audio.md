# Día 8 — IA generativa: vídeo y audio

**Módulo 2 · Desafíos y Avances en Inteligencia Artificial**

---

## Recapitulando el día anterior

Rápido:

> **Nombra los 6 elementos de un buen prompt de imagen.**

Si los recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 7 antes de continuar.

---

## De la imagen fija al movimiento y al sonido

Ayer aprendiste a controlar una imagen con sujeto, estilo, composición, luz, detalles técnicos y negativos. Hoy añades dos dimensiones nuevas: **el tiempo** (vídeo) y **el sonido** (audio). La lógica de fondo es la misma — cuanto más específico el prompt, menos improvisa el modelo — pero cada formato tiene sus propios elementos que controlar.

---

## La estructura de un buen prompt de vídeo

Un prompt de vídeo hereda los elementos de imagen (sujeto, estilo, luz) y añade los que tienen que ver con el movimiento:

| Elemento | Qué define | Ejemplo |
|---|---|---|
| **Sujeto y acción** | Qué o quién aparece, y qué hace *a lo largo del tiempo* | "Un barco navegando, acercándose lentamente a la cámara" |
| **Estilo visual** | Técnica: cinematográfico, animación, documental... | "estilo cinematográfico, grano de película" |
| **Movimiento de cámara** | Cómo se mueve el encuadre, no solo cómo está compuesto | "travelling lateral lento, sin cortes" |
| **Ritmo y duración** | Velocidad de la acción y duración del clip | "movimiento a cámara lenta, 5 segundos" |
| **Luz y ambiente** | Igual que en imagen, pero pensando en cómo cambia si hay movimiento | "luz de amanecer, niebla ligera sobre el agua" |
| **Negativos** | Qué evitar: cortes bruscos, deformaciones, texto | "sin cambios de plano, sin texto en pantalla" |

Ejemplo aplicando la plantilla:

> *"Un barco de pesca navegando y acercándose lentamente a la cámara al amanecer, con niebla ligera sobre el agua. Estilo cinematográfico con grano de película. Travelling lateral lento, movimiento a cámara lenta, 5 segundos, sin cortes. Sin texto en pantalla."*

### El mismo prompt en formato XML

```xml
<prompt_video>
  <sujeto_y_accion>Un barco de pesca navegando, acercándose lentamente a la cámara</sujeto_y_accion>

  <estilo>Cinematográfico, con grano de película</estilo>

  <movimiento_camara>Travelling lateral lento, sin cortes</movimiento_camara>

  <ritmo>
    <velocidad>Cámara lenta</velocidad>
    <duracion>5 segundos</duracion>
  </ritmo>

  <ambiente>
    <momento>Amanecer</momento>
    <atmosfera>Niebla ligera sobre el agua</atmosfera>
  </ambiente>

  <negativos>
    <evitar>Cortes de plano</evitar>
    <evitar>Texto en pantalla</evitar>
  </negativos>
</prompt_video>
```

**La diferencia clave frente a imagen:** en vídeo tienes que decidir qué cambia entre el primer y el último fotograma. Si no lo especificas (movimiento de cámara, ritmo), el modelo decide por ti — y suele generar movimientos genéricos o inconsistentes.

---

## La estructura de un buen prompt de audio

Aquí conviene separar dos casos: **música** y **voz/narración**, porque controlan cosas distintas.

### Para música

| Elemento | Qué define | Ejemplo |
|---|---|---|
| **Género/estilo** | Referencia musical | "lo-fi hip hop, synthwave, orquestal épico" |
| **Instrumentación** | Qué instrumentos suenan | "piano, cuerdas suaves, batería electrónica" |
| **Tempo y energía** | Ritmo y intensidad | "tempo lento, 80 BPM, relajante" |
| **Estructura** | Partes de la canción, si aplica | "intro instrumental, estrofa, estribillo pegadizo" |
| **Emoción/mood** | Sensación que debe transmitir | "melancólico pero esperanzador" |
| **Duración** | Longitud del clip | "30 segundos" |

Ejemplo:

> *"Pista lo-fi hip hop instrumental, con piano suave y batería electrónica relajada, tempo lento (80 BPM), mood melancólico pero cálido. Sin voz. Duración: 30 segundos."*

### Para voz/narración

| Elemento | Qué define | Ejemplo |
|---|---|---|
| **Texto exacto** | Qué se dice, palabra por palabra | El guion completo a narrar |
| **Tono de voz** | Emoción y estilo de entrega | "voz cálida y cercana, ritmo pausado" |
| **Tipo de voz** | Género, edad, acento si la herramienta lo permite | "voz femenina adulta, acento neutro" |
| **Uso** | Contexto: publicidad, audiolibro, tutorial | "narración de audiolibro, sin prisa" |

### El mismo prompt de música en formato XML

```xml
<prompt_audio>
  <genero>Lo-fi hip hop instrumental</genero>

  <instrumentacion>
    <instrumento>Piano suave</instrumento>
    <instrumento>Batería electrónica relajada</instrumento>
  </instrumentacion>

  <tempo>
    <bpm>80</bpm>
    <energia>Baja, relajante</energia>
  </tempo>

  <mood>Melancólico pero cálido</mood>

  <duracion>30 segundos</duracion>

  <negativos>
    <evitar>Voz o letra</evitar>
  </negativos>
</prompt_audio>
```

---

## Las herramientas: dónde generar vídeo y audio gratis

### Vídeo

| Herramienta | Motor | Gratis | Mejor para |
|---|---|---|---|
| **Sora** (vía ChatGPT) | Modelo de OpenAI | Generaciones limitadas en el plan free | Clips cortos con buena coherencia de escena |
| **Gemini / Veo** | Modelo de Google | Generaciones limitadas diarias | Integración con el resto del ecosistema Google, buena calidad general |
| **Runway** (Gen-3/4) | Modelo propio | Créditos gratis al registrarte | Control de movimiento de cámara y edición de vídeo con IA |
| **Luma Dream Machine** | Modelo propio | Generaciones gratis diarias | Vídeos realistas a partir de una imagen de referencia |
| **Kling** | Modelo propio (Kuaishou) | Créditos gratis diarios | Buena físico-realismo en movimiento de personas y objetos |
| **Pika** | Modelo propio | Créditos gratis limitados | Efectos y ediciones creativas rápidas |

### Audio

| Herramienta | Motor | Gratis | Mejor para |
|---|---|---|---|
| **Suno** | Modelo propio | Generaciones gratis diarias | Canciones completas con letra, estilo y voz generada |
| **Udio** | Modelo propio | Generaciones gratis diarias | Alternativa a Suno, buena calidad de instrumentación |
| **ElevenLabs** | Modelo propio | Minutos gratis al mes | Voz narrada realista y clonación de voz |
| **NotebookLM** (Google) | Modelo de Google | Gratis | Convertir texto en un "podcast" narrado automáticamente (lo veremos en el día 18) |

---


## Ejercicio 1 — Construye tu prompt de vídeo

Elige una escena simple (un objeto, un paisaje, una acción) y escribe un prompt de vídeo usando la plantilla: sujeto y acción, estilo, movimiento de cámara, ritmo/duración, ambiente y negativos.

Pruébalo en una de las herramientas gratuitas de vídeo.

<details>
<summary>Qué observar en el resultado</summary>

- ¿El movimiento de cámara que pediste se respeta o el modelo improvisa?
- ¿La duración y el ritmo son los que esperabas?
- ¿Qué pasa si no especificas movimiento de cámara? Prueba a quitarlo y compara.

</details>

---

## Ejercicio 2 — Construye tu prompt de audio

Elige entre música o narración de voz y escribe un prompt siguiendo la plantilla correspondiente. Genera el resultado en Suno, Udio o ElevenLabs según el caso.

> *Consejo:* si generas voz, prueba primero con un guion corto (2-3 frases) antes de narrar un texto largo — así detectas errores de pronunciación o de tono antes de gastar créditos.

---

## Ejercicio 3 — Combina vídeo + audio

Genera un clip de vídeo corto y una pista de música o narración pensada específicamente para acompañarlo (mismo mood, misma duración aproximada). No hace falta que las herramientas los unan automáticamente — el objetivo es practicar que ambos prompts compartan una misma dirección creativa.

---

## Trabajo en equipo — Duelo audiovisual

*(30 minutos)*

### El reto

Todos los equipos reciben el mismo brief: *"Anuncio de 10 segundos para una cafetería de especialidad, ambiente acogedor."*

Cada equipo genera:
1. Un clip de vídeo corto con la plantilla de vídeo
2. Una pista de música o narración con la plantilla de audio

Cada equipo usa herramientas distintas:

| Equipo | Vídeo | Audio |
|---|---|---|
| **Equipo 1** | Sora / Gemini Veo | Suno |
| **Equipo 2** | Runway | ElevenLabs (narración) |
| **Equipo 3** | Luma Dream Machine | Udio |
| **Equipo 4** | Kling o Pika | Suno o ElevenLabs |

### Votación

Cada equipo presenta su resultado (vídeo + audio, aunque no estén unidos en un solo archivo). El grupo vota cuál transmite mejor "ambiente acogedor" sin saber qué herramientas se usaron.

Debatid después:
- ¿El vídeo y el audio elegidos encajaban en mood, o iban por caminos distintos?
- ¿Qué equipo tuvo que iterar más para conseguir algo usable?
- ¿Dónde veis aplicación real de esto en vuestro trabajo (redes sociales, presentaciones, publicidad)?

---

## Lo que aprendiste hoy

- Un prompt de vídeo añade movimiento de cámara, ritmo y duración a los elementos de imagen
- Si no especificas el movimiento de cámara, el modelo decide por ti — y suele ser genérico
- Un prompt de audio de música controla género, instrumentación, tempo y mood; uno de voz controla texto exacto, tono y tipo de voz
- Existen herramientas gratuitas de calidad para vídeo (Runway, Luma, Kling, Pika) y audio (Suno, Udio, ElevenLabs)
- Este es el terreno de la IA generativa que más rápido evoluciona — conviene revisar el estado del arte con frecuencia

---

*Mañana: IA para código y agentes — Copilot, Cursor y Claude Code.*
