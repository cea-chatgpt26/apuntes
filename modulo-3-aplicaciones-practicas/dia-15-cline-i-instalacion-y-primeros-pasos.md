# Día 15 — Cline I: instalación y primeros pasos

**Módulo 3 · Aplicaciones Prácticas y Proyecto**

---

## Recapitulando el día anterior

Rápido:

> **¿Para qué sirve el Data Store en Make, y qué problema resuelve que un módulo normal no puede resolver por sí solo?**

Si lo recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 14 antes de continuar.

---

## De agentes que automatizan a agentes que escriben y ejecutan

En el día 9 conociste a **Claude Code**, un agente que trabaja desde la terminal, lee un proyecto entero y escribe, ejecuta y corrige código sin supervisión paso a paso — y dijimos que no lo ibais a usar en este curso. Hoy tocamos esa promesa: vais a instalar y usar **Cline**, un agente con la misma filosofía pero integrado directamente en un editor de código (Visual Studio Code), con una diferencia clave para vosotros: **cada cambio que propone se revisa antes de aplicarse**, como una propuesta que aceptas o rechazas, no una caja negra.

No hace falta saber programar para el día de hoy. El objetivo es perder el miedo al editor de código y entender cómo se le da instrucciones a un agente que trabaja sobre archivos reales — una habilidad que cada vez pesa más, sepas programar o no, porque cambia radicalmente cómo se construyen herramientas digitales.

---

## Qué es Cline

Cline es una **extensión de Visual Studio Code** que convierte el editor en un agente de IA: le escribes lo que quieres conseguir en lenguaje natural, y Cline decide qué archivos crear o modificar, te muestra el cambio propuesto como un **diff** (una comparación de "antes/después"), y solo lo aplica si tú lo apruebas.

| | ChatGPT / Gemini (chat normal) | Cline |
|---|---|---|
| **Dónde vive** | En una web o app aparte | Dentro del editor de código, con acceso directo a los archivos del proyecto |
| **Qué te devuelve** | Texto o código que tú copias y pegas a mano | Cambios ya aplicados (o propuestos) directamente sobre los archivos reales |
| **Contexto** | Solo lo que le pegas en el chat | Puede leer archivos enteros del proyecto por sí mismo, sin que se los pegues |
| **Ejecución** | No ejecuta nada por ti | Puede ejecutar comandos en la terminal (instalar algo, correr un script) si se lo permites |

La idea central de hoy: **Cline no reemplaza tu criterio, lo multiplica** — tú sigues decidiendo qué se acepta, pero dejas de escribir cada línea a mano.

---

## Instalación y configuración

Pasos para tener Cline funcionando:

1. **Instala Visual Studio Code** (si no lo tienes) desde su sitio oficial — es gratuito.
2. Abre la pestaña de **extensiones** (icono de cuadraditos en la barra lateral) y busca "**Cline**". Instálala.
3. Cline necesita conectarse a un modelo de IA para funcionar — normalmente pide una **API key** (de Anthropic, OpenAI o similar). Es una conexión parecida a la que hiciste con OpenAI en Make (día 13), pero aquí alimenta directamente al editor.
4. Al abrir Cline por primera vez, verás un panel lateral con un chat — ese chat es el punto de entrada para darle instrucciones.

<details>
<summary>Si no tienes API key propia</summary>

Algunos planes de Cline permiten probarlo con crédito gratuito inicial, sin necesidad de configurar tu propia key el primer día. Si tu centro o instructor os da acceso compartido, usad ese mientras exploráis — configurar vuestra propia key es sencillo y lo podéis hacer después.

</details>

---

## Plan Mode y Act Mode

Cline tiene dos modos de trabajo, y entender la diferencia es la base de todo lo que harás hoy y mañana:

| Modo | Qué hace | Cuándo usarlo |
|---|---|---|
| **Plan** | Cline piensa y te propone un plan de qué va a hacer, pero **no toca ningún archivo todavía** | Tareas nuevas o poco claras, donde quieres revisar el enfoque antes de que se ejecute nada |
| **Act** | Cline ejecuta los cambios: crea o edita archivos, y te los muestra como un diff que apruebas paso a paso | Cuando ya tienes claro qué quieres y el plan (si lo hubo) te convence |

El flujo recomendado para empezar: **Plan → revisar → Act**. Igual que en Make revisabas con Run once antes de activar un escenario, aquí revisas el plan antes de dejar que Cline toque nada.

---

## Cómo darle una buena instrucción a Cline

Las mismas reglas de un buen prompt que viste en los días 4 y 5 (rol, contexto, formato, few-shot) siguen aplicando, con un añadido: aquí puedes **decirle a Cline qué archivos mirar**, en vez de pegarle el contenido a mano.

Una instrucción bien construida tiene:

- **Objetivo concreto:** qué quieres conseguir, no solo "mejora esto"
- **Contexto de archivos:** si el proyecto ya tiene algo relacionado, dile a Cline que lo revise antes de crear algo nuevo desde cero
- **Restricciones:** qué no debe tocar o cambiar (por ejemplo, "no modifiques el archivo de configuración")

Ejemplo de instrucción floja: *"Hazme una web."*
Ejemplo de instrucción sólida: *"Crea una página web de una sola pantalla (HTML+CSS, sin frameworks) para presentar un servicio de reparación de bicicletas: título, 3 servicios con precio, y un formulario de contacto simple. No uses ningún archivo fuera de esta carpeta."*

---

## Antes de empezar: prueba guiada

Crea una carpeta nueva y vacía en tu ordenador, ábrela en VS Code, y pídele a Cline (en **Plan mode**) que te proponga cómo crear una página web sencilla de una sola pantalla con tu nombre y una breve presentación. Revisa el plan, pásate a **Act mode**, y aprueba los cambios paso a paso hasta ver el resultado.

<details>
<summary>Cómo comprobar el resultado</summary>

Abre el archivo HTML que Cline haya creado directamente en el navegador (clic derecho → abrir con navegador, o arrastra el archivo a una pestaña nueva). Si algo no se ve bien, vuelve al chat de Cline y pídele el ajuste concreto — no hace falta que lo edites tú a mano.

</details>

---

## Catálogo de ejercicios — elige tu ruta

No hace falta hacerlos todos. Elige al menos uno de Nivel 1, uno de Nivel 2, y si te sobra tiempo, prueba uno de Nivel 3.

### Nivel 1 — Crear un archivo desde cero

| Ámbito | Tarea a pedirle a Cline |
|---|---|
| **Presentación personal / portfolio** | Una página web de una sola pantalla con tu presentación profesional y forma de contacto |
| **Documentación** | Un archivo de texto con una plantilla de brief de proyecto reutilizable (como la del día 10-11, pero la tuya propia) |
| **Organización personal** | Una lista de tareas en HTML simple, con casillas que se puedan marcar como hechas |
| **Negocio / freelance** | Una página de "menú de servicios" con nombre, descripción y precio de 3-4 servicios |
| **Educación / formación** | Una página con un cuestionario de 5 preguntas de autoevaluación sobre un tema que domines |

<details>
<summary>Qué comprobar al terminar</summary>

- Usaste Plan mode antes de Act mode al menos una vez
- Revisaste el diff propuesto antes de aceptarlo, en lugar de aceptar todo sin mirar

</details>

---

### Nivel 2 — Modificar algo que ya existe

Pide a Cline que **cambie** algo del archivo del Nivel 1 (o de cualquier archivo simple que ya tengas), sin crearlo desde cero.

| Ámbito | Tarea a pedirle a Cline |
|---|---|
| **Presentación personal / portfolio** | Cambiar los colores y la tipografía de tu página para que combinen con un estilo concreto (por ejemplo, "minimalista y oscuro") |
| **Documentación** | Añadir una sección nueva a tu plantilla de brief sin romper el formato de las secciones existentes |
| **Organización personal** | Añadir una fecha límite a cada tarea de tu lista, y que las vencidas se marquen en rojo |
| **Negocio / freelance** | Añadir un cuarto servicio a tu página de menú, manteniendo el mismo formato que los otros tres |
| **Educación / formación** | Añadir una puntuación final automática a tu cuestionario de autoevaluación |

<details>
<summary>Dónde se suele atascar la gente en este nivel</summary>

- Pedir un cambio muy vago ("mejóralo") y que Cline toque más de lo esperado — sé específico sobre qué parte del archivo debe cambiar y cuál debe quedarse igual
- No revisar el diff con calma: es la única forma de detectar si Cline ha tocado algo que no le pediste

</details>

---

### Nivel 3 — Varios archivos relacionados

| Ámbito | Tarea a pedirle a Cline |
|---|---|
| **Presentación personal / portfolio** | Separar tu página en dos archivos (HTML y CSS aparte) y que Cline los conecte correctamente |
| **Documentación** | Un pequeño conjunto de 2-3 archivos de notas enlazados entre sí (un índice + páginas de contenido) |
| **Organización personal** | Una lista de tareas que guarde los datos en un archivo aparte, para que no se pierdan al cerrar la página |
| **Negocio / freelance** | Una página de menú de servicios + una página de contacto separada, enlazadas entre sí |
| **Educación / formación** | Un cuestionario con las preguntas en un archivo aparte de la lógica que las muestra, para poder añadir preguntas fácilmente |

<details>
<summary>Pista técnica</summary>

Cuando el proyecto tiene varios archivos, Cline necesita que le indiques (o que él mismo detecte) cómo se relacionan. Si algo no encaja, pídele explícitamente que revise todos los archivos del proyecto antes de proponer el cambio — así evitas que trabaje con información incompleta.

</details>

---

### Nivel 4 (reto opcional) — De cero a funcionando, sin tocar código a mano

Elige cualquier idea de las anteriores (o una tuya) y complétala de principio a fin usando únicamente instrucciones en lenguaje natural — sin editar directamente ni una línea de código, solo aprobando o rechazando lo que Cline propone.

<details>
<summary>Cómo saber que lo has conseguido</summary>

Si en algún momento tuviste que abrir el archivo y escribir código tú mismo para arreglar algo, anótalo — es la pista de qué instrucción podrías haber dado mejor a Cline para que lo resolviera él solo.

</details>

---

## Trabajo en equipo — Mismo objetivo, instrucciones distintas

*(25 minutos)*

### El reto

En parejas, elegid la misma idea del catálogo (por ejemplo, la página de menú de servicios) pero **cada persona la construye con Cline por separado, con su propia forma de dar instrucciones**. Al terminar, comparad los dos resultados.

### Puesta en común

- ¿Qué diferencias hay entre los dos resultados, y a qué instrucción concreta se debe cada diferencia?
- ¿En qué momento usasteis Plan mode y en cuál Act mode directamente? ¿Por qué?
- ¿Hubo algún cambio que rechazasteis porque Cline propuso algo que no queríais? ¿Qué instrucción lo habría evitado?

---

## Lo que aprendiste hoy

- Cline es un agente de IA integrado en VS Code que crea y modifica archivos reales, mostrando cada cambio como un diff que apruebas o rechazas
- **Plan mode** propone un enfoque sin tocar archivos; **Act mode** ejecuta los cambios paso a paso con tu aprobación
- Una buena instrucción para Cline combina objetivo concreto, contexto de archivos existentes y restricciones claras — los mismos principios de prompt de los días 4 y 5
- Revisar el diff antes de aceptarlo es la parte del proceso que no deberías saltarte nunca, aunque parezca lento al principio
- Mañana vas más allá de tareas sueltas: instrucciones con más contexto, varios archivos a la vez, y reglas propias que Cline respeta en todo el proyecto

---

*Mañana: Cline II — flujos de trabajo reales, con más contexto y tareas de varios pasos.*
