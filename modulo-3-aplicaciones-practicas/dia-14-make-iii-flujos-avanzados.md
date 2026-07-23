# Día 14 — Make III: flujos avanzados

**Módulo 3 · Aplicaciones Prácticas y Proyecto**

---

## Recapitulando el día anterior

Rápido:

> **¿Por qué es importante pedirle a la IA un formato de salida estricto cuando su respuesta va a alimentar un Router?**

Si lo recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 13 antes de continuar.

---

## De un flujo que funciona a un flujo que aguanta

En los dos días anteriores construiste escenarios que funcionan **cuando todo sale bien**: llega un dato, un módulo lo procesa, la IA decide, el siguiente módulo actúa. Hoy es el último día del mini-proyecto (recuerda el calendario del brief: días 12-14), así que toca lo que separa una demo de una automatización real:

- ¿Qué pasa si el trigger trae **varios elementos a la vez**, no uno solo?
- ¿Qué pasa si necesitas **recordar algo** entre una ejecución y la siguiente?
- ¿Qué pasa si un módulo **falla** — la API no responde, el dato viene vacío, la IA devuelve algo raro?

Estas tres preguntas son las que hoy conviertes en piezas concretas de tu escenario, y con eso cierras la primera versión completa de tu mini-proyecto.

---

## Iterator y Aggregator: cuando hay varios elementos, no uno

Hasta ahora tus escenarios procesaban un dato a la vez (un email, una fila, un lead). Pero muchos triggers reales traen **una lista**: todas las filas nuevas de una hoja, todos los adjuntos de un email, todos los productos de un pedido.

| Módulo | Qué hace |
|---|---|
| **Iterator** | Coge una lista (array) y la convierte en ejecuciones individuales, una por elemento, para que el resto del flujo procese cada uno por separado |
| **Aggregator** | Hace lo contrario: coge varias ejecuciones individuales y las junta de nuevo en una sola lista o en un único texto/documento |

Ejemplo típico: un pedido con 5 productos → **Iterator** separa cada producto → un módulo de IA genera una descripción para cada uno → **Aggregator** junta las 5 descripciones en un único email de confirmación.

Sin el Iterator, Make trataría el pedido entero como un solo bloque de datos y no podrías procesar producto por producto; sin el Aggregator, acabarías enviando 5 emails sueltos en vez de uno solo bien compuesto.

---

## Data Store: cuando el flujo necesita memoria

Cada ejecución de un escenario, por defecto, no sabe nada de las ejecuciones anteriores. Eso es un problema si necesitas evitar duplicados o llevar la cuenta de algo (cuántas veces ha pasado esto, si ya se procesó este email...).

El **Data Store** de Make es justo eso: una tabla de datos que persiste entre ejecuciones, a la que el escenario puede leer y escribir.

Casos donde hace falta:

- Evitar procesar el mismo email dos veces si el escenario se ejecuta cada 15 minutos
- Llevar un contador (cuántas solicitudes ha habido hoy) sin depender de una hoja externa
- Guardar el último ID procesado, para que la siguiente ejecución solo mire lo nuevo

---

## Manejo de errores: que un fallo no tumbe todo el escenario

Un escenario en producción falla tarde o temprano: una API externa no responde, un campo llega vacío, la IA devuelve un formato inesperado. Sin manejo de errores, **un solo fallo detiene todo el escenario** y las siguientes ejecuciones dejan de dispararse hasta que lo reactivas a mano.

Make permite añadir un **manejador de errores** a cualquier módulo, con varias estrategias:

| Estrategia | Qué hace | Cuándo usarla |
|---|---|---|
| **Ignore** | Ignora el error y sigue con el resto del flujo | El paso que falla no es crítico (por ejemplo, un log opcional) |
| **Resume** | Sigue el flujo con un valor por defecto en lugar del que falló | Tienes un valor razonable de respaldo (ej. "Sin clasificar" si la IA no responde) |
| **Retry** | Reintenta el módulo un número de veces antes de rendirse | Errores temporales, típicos de APIs externas (rate limits, timeouts) |
| **Break / Rollback** | Detiene ese elemento concreto (útil junto al Iterator) sin tumbar toda la ejecución | Un elemento de una lista falla, pero el resto debe seguir procesándose |

**La regla práctica:** cualquier módulo que dependa de una IA o de una API externa merece, como mínimo, un **Retry**. Cualquier dato crítico para decidir una ruta merece un valor de **Resume** por defecto, para que el escenario nunca se quede "colgado" esperando algo que no va a llegar.

---

## Antes de empezar: prueba guiada

Coge un escenario de los días anteriores que use un módulo de OpenAI y añádele un manejador de error tipo **Retry** (2-3 intentos). Simula un fallo si puedes (por ejemplo, desconectando temporalmente la cuenta) y comprueba con **Run once** que el escenario reintenta en lugar de romperse a la primera.

<details>
<summary>Si no puedes forzar un fallo real</summary>

No pasa nada — basta con que configures el manejador y entiendas dónde se añade (clic derecho sobre el módulo → "Add error handler"). Lo importante hoy es saber que existe y cuándo usarlo, no haberlo visto fallar en directo.

</details>

---

## Catálogo de ejercicios — elige tu ruta

Igual que los días anteriores: no hace falta hacerlos todos. Elige al menos uno de Nivel 1, uno de Nivel 2, y si te sobra tiempo, prueba uno de Nivel 3. Intenta que al menos uno se parezca al problema real de tu mini-proyecto — hoy es el día de cerrarlo.

### Nivel 1 — Iterator + Aggregator

| Ámbito | Automatización a construir |
|---|---|
| **Atención al cliente** | Hoja con varios tickets abiertos → Iterator los separa uno a uno → IA genera una prioridad para cada uno → Aggregator junta el resultado en un único informe diario |
| **Ventas / CRM** | Lista de leads del día → Iterator los separa → IA genera un mensaje de seguimiento personalizado para cada uno → Aggregator los junta en un solo email para revisión del comercial |
| **Marketing / redes** | Lista de productos nuevos en una hoja → Iterator los separa → IA genera una descripción para cada uno → Aggregator junta todas las descripciones en un documento único |
| **RRHH** | Lista de candidatos de la semana → Iterator los separa → IA genera un resumen de cada perfil → Aggregator compone un informe único para el responsable de selección |
| **Administración** | Varias facturas recibidas en un día → Iterator las separa → se extrae el importe de cada una → Aggregator suma el total y genera un resumen diario |
| **Logística / inventario** | Lista de productos con stock bajo → Iterator los separa → se genera una alerta por producto → Aggregator junta todas las alertas en un único email al responsable de compras |

<details>
<summary>Qué comprobar al terminar</summary>

- El Iterator genera tantas ejecuciones como elementos había en la lista original — compruébalo en el historial de ejecuciones
- El Aggregator produce un único resultado final, no una lista sin procesar

</details>

---

### Nivel 2 — Data Store para evitar duplicados o llevar memoria

| Ámbito | Automatización a construir |
|---|---|
| **Atención al cliente** | Escenario que revisa una bandeja cada 15 minutos → Data Store guarda el ID del último email procesado, para no notificar el mismo dos veces |
| **Ventas / CRM** | Escenario que registra leads nuevos → Data Store lleva la cuenta de cuántos leads ha habido esta semana, y lo incluye en un resumen |
| **Marketing / redes** | Escenario que publica contenido programado → Data Store guarda qué publicaciones ya se han hecho, para no repetir la misma dos veces |
| **RRHH** | Escenario que procesa solicitudes de vacaciones → Data Store guarda los días ya aprobados por persona, para detectar solapamientos |
| **Administración** | Escenario que procesa facturas → Data Store guarda los números de factura ya procesados, para no duplicar el registro si el email llega dos veces |
| **Logística / inventario** | Escenario que revisa el stock → Data Store guarda cuándo fue la última alerta enviada por producto, para no saturar con avisos repetidos |

<details>
<summary>Dónde se suele atascar la gente en este nivel</summary>

- Olvidar que hay que **comprobar primero** si el dato ya existe en el Data Store antes de decidir si actuar o no (normalmente con un Router justo después del módulo de búsqueda del Data Store)
- Configurar el Data Store sin definir bien la clave (key) que identifica cada registro, lo que hace que nunca detecte duplicados correctamente

</details>

---

### Nivel 3 — Manejo de errores en un flujo con IA

| Ámbito | Automatización a construir |
|---|---|
| **Atención al cliente** | Email → clasificación por IA con manejador **Retry** (si la API falla, reintenta 3 veces) → si sigue fallando, **Resume** con valor "Sin clasificar" para que el ticket no se pierda |
| **Ventas / CRM** | Generación de email de seguimiento con IA → **Retry** ante fallo de conexión → si falla definitivamente, se notifica al comercial para que lo escriba a mano en vez de bloquear el flujo |
| **Marketing / redes** | Generación de descripción de producto con IA → **Resume** con un texto genérico por defecto si la IA no responde, para no dejar el producto sin publicar |
| **RRHH** | Resumen de CV con IA dentro de un Iterator (varios candidatos) → **Break** en el candidato que falla, para que el resto del lote se siga procesando sin interrumpirse |
| **Administración** | Extracción de importe de factura con IA → si el importe no se puede leer, **Resume** enviando el caso a revisión manual en lugar de fallar en silencio |
| **Logística / inventario** | Alerta de stock generada con IA dentro de un Iterator → **Ignore** en errores no críticos (por ejemplo, un producto sin descripción) para no frenar el resto de alertas |

<details>
<summary>Pista técnica</summary>

El manejador de error se añade sobre el módulo concreto que puede fallar, no sobre todo el escenario. Prueba distintas estrategias en el mismo módulo para ver cómo cambia el comportamiento del resto del flujo — es la mejor forma de entender la diferencia entre Ignore, Resume, Retry y Break.

</details>

---

### Nivel 4 (reto opcional) — Cierra tu mini-proyecto completo

Hoy es el último día dedicado al mini-proyecto. El reto es dejarlo funcionando de principio a fin, integrando lo aprendido en los tres días de Make:

- Trigger real (día 12)
- Al menos un módulo de OpenAI con Router condicional (día 13)
- Al menos una de las piezas de hoy: Iterator/Aggregator, Data Store o manejo de errores

<details>
<summary>Cómo saber que está "cerrado"</summary>

Ejecuta el escenario completo con **Run once** de principio a fin, sin intervenir manualmente en ningún módulo intermedio, y comprueba que el resultado final es el que esperabas según tu brief original.

</details>

---

## Cierra tu mini-proyecto

Vuelve al escenario que has ido construyendo estos tres días para tu propio proyecto y añade, como mínimo, **una** de las piezas de hoy (Iterator, Data Store o manejo de errores) allí donde tenga sentido. Con eso, el mini-proyecto queda cerrado como primera pieza de tu portfolio — más adelante (días 15-19) lo ampliarás con contenido generado por IA hasta llegar al proyecto grande.

<details>
<summary>Qué apuntar</summary>

- ¿Qué parte de tu flujo era más frágil, y qué manejador de error le añadiste?
- ¿Tu flujo necesita procesar varios elementos a la vez (Iterator), o siempre trabaja con uno solo?

</details>

---

## Trabajo en equipo — Reto por parejas

*(25 minutos)*

### El reto

En parejas, coged un escenario ya construido en días anteriores (vuestro o de un ejercicio del catálogo) y añadidle **una pieza nueva de hoy** que no tuviera: Iterator/Aggregator, Data Store, o un manejador de error.

### Puesta en común

- ¿Qué pieza añadisteis y qué problema resolvía?
- ¿Qué pasaba en el escenario *antes* de añadirla, si el dato llegaba en lista, se repetía o fallaba un módulo?
- De las tres piezas de hoy, ¿cuál creéis que os hará falta más a menudo en vuestro propio trabajo?

---

## Lo que aprendiste hoy

- El **Iterator** separa una lista en elementos individuales; el **Aggregator** los vuelve a juntar en un único resultado
- El **Data Store** da memoria a un escenario entre ejecuciones — clave para evitar duplicados o llevar contadores
- Un manejador de error (**Ignore, Resume, Retry, Break**) evita que un fallo puntual tumbe todo el escenario
- Cualquier módulo que dependa de una IA o una API externa debería tener, como mínimo, un Retry
- Tu mini-proyecto ya está cerrado de principio a fin — es la primera pieza de tu portfolio, y desde el día 15 empiezas a construir el proyecto grande sobre esta misma base

---

*Mañana: Cline I — instaláis y dais vuestros primeros pasos con un agente de IA dentro de Visual Studio Code.*
