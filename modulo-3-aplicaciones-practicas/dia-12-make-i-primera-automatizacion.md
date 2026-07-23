# Día 12 — Make I: primera automatización

**Módulo 3 · Aplicaciones Prácticas y Proyecto**

---

## Recapitulando el día anterior

Rápido:

> **¿Qué obligación legal tienes en la UE si generas contenido con IA que se hace pasar por real?**

Si lo recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 11 antes de continuar.

---

## De entender agentes a construir uno

En el día 9 viste qué es un agente: algo que persigue un objetivo y encadena pasos por sí solo. Hoy dejáis de ser espectadores y empezáis a construir: **Make** es la herramienta con la que vais a montar vuestra primera automatización sin escribir una línea de código.

Es también el arranque del **mini-proyecto** (días 12-14) que definiste ayer en tu brief — hoy construyes la primera versión, mínima, de esa idea.

---

## Qué es Make

Make (antes Integromat) es una herramienta **no-code** para conectar aplicaciones y automatizar tareas repetitivas: cuando pasa algo en una app, Make hace algo en otra, sin que tengas que intervenir manualmente cada vez.

La lógica es siempre la misma:

> **Cuando ocurre X (disparador) → haz Y (una o varias acciones)**

Ejemplos cotidianos de esto que probablemente ya conoces sin llamarlo "automatización":

- Cuando alguien rellena un formulario → se añade una fila a una hoja de cálculo
- Cuando llega un email con una factura → se guarda el adjunto en una carpeta
- Cuando se publica un post → se envía un aviso a un canal de Slack

---

## Los tres bloques de un escenario

En Make, cada automatización se llama **escenario**. Todo escenario se construye con tres piezas:

| Bloque | Qué es | Ejemplo |
|---|---|---|
| **Trigger (disparador)** | El evento que arranca el escenario | Llega un email nuevo, se envía un formulario, pasa una hora concreta |
| **Módulos (acciones)** | Los pasos que se ejecutan después del trigger, en orden | Guardar un dato, enviar un mensaje, crear un archivo |
| **Conexiones** | Las cuentas de las apps que Make necesita para actuar en tu nombre | Tu cuenta de Gmail, Google Sheets, Slack... |

Un escenario mínimo tiene **un trigger + al menos un módulo**. A partir de ahí se puede encadenar todo lo que haga falta — eso lo veréis en los días 13 y 14.

---

## Tour por la interfaz

Antes de construir nada, familiarízate con dónde está cada cosa al entrar en Make:

- **Lienzo (canvas):** el espacio central donde se colocan y conectan los módulos, de izquierda a derecha
- **Botón "+" para añadir módulos:** cada módulo representa una app (Gmail, Sheets, Slack...) y una acción dentro de esa app
- **Panel de configuración de cada módulo:** se abre al hacer clic en un módulo; aquí defines qué datos usa y de dónde los saca
- **Botón Run once:** ejecuta el escenario una sola vez manualmente, para probarlo sin esperar a que ocurra el trigger real
- **Interruptor ON/OFF (Scheduling):** activa o desactiva el escenario para que se ejecute solo cuando ocurra el trigger

---

## Antes de empezar: prueba guiada

Crea una cuenta gratuita en Make (si no la tienes) y monta un escenario mínimo — **trigger + un módulo** — antes de pasar al catálogo de ejercicios. Un buen primero: **trigger "Schedule" (a una hora fija) → módulo que te envíe un email**. Usa **Run once** para probarlo sin esperar al disparador real; si algo falla, Make marca en rojo el módulo con el error.

Con eso funcionando, ya tienes soltura para atacar el catálogo de abajo.

---

## Catálogo de ejercicios — elige tu ruta

A partir de aquí, el día es fundamentalmente práctico: un catálogo de automatizaciones de ejemplo, organizadas por **nivel de dificultad** y por **ámbito**. No hace falta hacerlas todas — elige al menos una de Nivel 1, una de Nivel 2, y si te sobra tiempo, prueba una de Nivel 3. Intenta que al menos una de las que elijas se parezca al problema real de tu mini-proyecto.

### Nivel 1 — Trigger + una acción

El objetivo es soltura básica: conectar un disparador con una única acción, sin lógica adicional.

| Ámbito | Automatización a construir |
|---|---|
| **Atención al cliente** | Cuando llega un email nuevo a una bandeja → se reenvía automáticamente a otra dirección o canal |
| **Ventas / CRM** | Cuando se añade una fila nueva en una hoja de leads → se envía una notificación por email |
| **Marketing / redes** | A una hora programada cada día → se envía un recordatorio con la tarea de contenido del día |
| **RRHH** | Cuando alguien rellena un formulario de "alta de empleado" → se crea automáticamente una fila en una hoja de seguimiento |
| **Administración** | Cuando llega un email con la palabra "factura" en el asunto → se guarda el adjunto en una carpeta de Drive |
| **Educación / formación** | Cuando un alumno entrega un formulario → se le envía automáticamente un email de confirmación de recepción |

<details>
<summary>Qué comprobar al terminar</summary>

- El trigger detecta el evento sin que tengas que forzarlo manualmente
- La acción se ejecuta con el dato correcto (no un valor de prueba fijo, sino el dato real que llegó por el trigger)

</details>

---

### Nivel 2 — Trigger + dos o tres acciones encadenadas

Aquí el reto es pasar datos de un módulo a otro: lo que genera el paso 1 lo usa el paso 2.

| Ámbito | Automatización a construir |
|---|---|
| **Atención al cliente** | Nuevo mensaje en un formulario de contacto → se guarda en una hoja de registro → se envía un aviso a un canal de equipo |
| **Ventas / CRM** | Nuevo lead en una hoja → se añade a una lista de contactos → se envía un email de bienvenida automático |
| **Marketing / redes** | Se publica un evento en un calendario → se crea un recordatorio → se envía un email al equipo con la fecha y los detalles |
| **RRHH** | Se recibe una solicitud de vacaciones por formulario → se registra en una hoja de control → se notifica al responsable por email |
| **Administración** | Llega una factura por email → se guarda el adjunto en Drive → se añade una fila en una hoja con el nombre del archivo y la fecha |
| **Logística / inventario** | El stock de un producto (en una hoja) baja de un número concreto → se registra una alerta → se envía un aviso al responsable de compras |

<details>
<summary>Dónde se suele atascar la gente en este nivel</summary>

- Olvidar que el dato de un módulo (por ejemplo, el email del remitente) hay que **mapearlo explícitamente** en el siguiente módulo, no aparece solo
- No probar con **Run once** después de cada módulo nuevo, y descubrir el error tres pasos más tarde

</details>

---

### Nivel 3 — Con condición (router o filtro)

Introduce una decisión: el flujo hace una cosa u otra según el dato que llega. Todavía no habéis visto el módulo de IA (eso es mañana) — aquí la condición se basa en datos simples: texto, número o fecha.

| Ámbito | Automatización a construir |
|---|---|
| **Atención al cliente** | Nuevo email recibido → si el asunto contiene "urgente" se notifica por un canal prioritario, si no, se registra en una hoja para revisar más tarde |
| **Ventas / CRM** | Nuevo lead en una hoja → si el presupuesto indicado supera un umbral, se notifica al equipo comercial; si no, se añade a una lista de seguimiento general |
| **Marketing / redes** | Publicación programada → si la fecha es fin de semana, se pospone al lunes; si es entre semana, se publica según lo previsto |
| **RRHH** | Solicitud de vacaciones → si las fechas coinciden con otra solicitud ya registrada, se marca como conflicto; si no, se aprueba automáticamente el registro |
| **Administración** | Factura recibida por email → si el importe supera un límite, se envía a un responsable para validación manual; si no, se archiva directamente |
| **Logística / inventario** | Nueva fila de pedido → si la cantidad supera el stock disponible, se genera una alerta de reposición; si no, se marca como pedido listo |

<details>
<summary>Pista técnica</summary>

En Make esto se hace con un **Router** (divide el flujo en varias rutas, cada una con un filtro) o con un **Filter** en un único camino (solo deja pasar los datos que cumplen la condición). No necesitas más que eso para completar estos ejercicios — el resto de lógica condicional avanzada lo veréis en el día 13.

</details>

---

### Nivel 4 (reto opcional) — Tu propio caso, desde cero

Diseña y construye una automatización completa para un problema real de tu día a día o del sector al que quieres volver, sin plantilla dada. Debe tener como mínimo trigger + dos acciones, y si te atreves, una condición.

<details>
<summary>Cómo elegir el caso</summary>

Piensa en una tarea que repites cada semana y que sigue siempre el mismo patrón: "cuando pasa esto, siempre hago aquello". Si te cuesta encontrar una, vuelve a tu brief del mini-proyecto (día 10-11) — probablemente ya tienes ahí un candidato perfecto.

</details>

---

## Conecta el disparador con tu mini-proyecto

Antes de acabar el día, vuelve a tu brief y monta en Make **el trigger real de tu mini-proyecto** (aunque el resto del flujo todavía esté vacío o sea muy simple). Es la base sobre la que seguirás construyendo en los días 13 y 14.

<details>
<summary>Qué apuntar</summary>

- ¿Qué app dispara el flujo?
- ¿Qué dato necesitas capturar en ese primer paso para poder usarlo después?

</details>

---

## Trabajo en equipo — Reto por parejas

*(25 minutos)*

### El reto

En parejas, elegid **un ejercicio de Nivel 2 o Nivel 3 del catálogo** (de un ámbito distinto al de vuestro propio proyecto) y construidlo completo en Make antes de que se acabe el tiempo.

### Puesta en común

- ¿Qué ámbito y ejercicio elegisteis, y por qué?
- ¿Dónde os atascasteis: en el trigger, en pasar datos entre módulos, o en la condición (si la había)?
- ¿Qué habríais tardado en hacer esto mismo a mano, sin Make?

---

## Lo que aprendiste hoy

- Make conecta aplicaciones con la lógica "cuando ocurre X → haz Y", sin necesidad de programar
- Todo escenario se construye con tres piezas: trigger, módulos (acciones) y conexiones a las apps
- **Run once** te permite probar un escenario paso a paso sin esperar al trigger real
- Un **Router** o **Filter** permite que el flujo tome caminos distintos según el dato que llega, sin usar IA todavía
- Las mismas automatizaciones (aviso, registro, alerta condicional) se repiten en casi cualquier ámbito: atención al cliente, ventas, RRHH, marketing o administración
- Ya tienes montado el primer trigger de tu mini-proyecto — mañana lo conectas con IA

---

*Mañana: Make II — el nodo de OpenAI y la lógica condicional para que tu flujo tome decisiones.*
