# Día 19 — Integración total

**Módulo 3 · Aplicaciones Prácticas y Proyecto**

---

## Recapitulando el día anterior

Rápido:

> **¿Qué problema resuelve NotebookLM que un chat normal no resuelve bien?**

Si lo recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 18 antes de continuar.

---

## El día de juntar todas las piezas

Llevas ocho días construyendo piezas sueltas: un trigger en Make (día 12), un módulo de OpenAI con Router condicional (día 13), Iterator, Data Store y manejo de errores (día 14), y contenido o insumos generados con IA (días 15-16 con Cline y día 18 con Perplexity/NotebookLM/Gamma). Hoy no hay contenido nuevo que aprender — **hoy es un día 100% de construcción**: juntáis todas esas piezas en el proyecto grande que presentaréis mañana.

---

## Qué diferencia al proyecto grande del mini-proyecto

| | Mini-proyecto (días 12-14) | Proyecto grande (hoy) |
|---|---|---|
| **Alcance** | Trigger + 1-3 acciones, versión mínima | El flujo completo de vuestro brief, de principio a fin |
| **Contenido generado por IA** | Poco o ninguno | Integrado en el flujo: texto, imagen, vídeo o audio real |
| **Manejo de errores** | Opcional | Recomendado en cualquier paso que dependa de una IA o API externa (día 14) |
| **Objetivo** | Aprender la mecánica de Make | Pieza de portfolio lista para enseñar a un empleador |

No partís de cero: el mini-proyecto ya os dio el trigger y la estructura base. Hoy la ampliáis.

---

## Checklist antes de empezar a construir

Antes de tocar Make, repasad estos tres documentos que habéis ido generando:

1. **Vuestro brief** (día 10-11): el problema, el trigger, qué genera la IA, el resultado esperado.
2. **Vuestro mini-proyecto** (días 12-14): el escenario base ya construido en Make.
3. **Vuestros insumos** (día 18): el texto, imagen o presentación que preparasteis ayer.

Si te falta alguno de los tres, complétalo antes de avanzar — el resto del día depende de tenerlos claros.

---

## Guía de construcción: de mini-proyecto a proyecto grande

No es un catálogo de ejercicios como los días de Make — es una guía de pasos que aplicáis directamente sobre vuestro propio proyecto:

### Paso 1 — Revisa y amplía el trigger

Vuelve al trigger de tu mini-proyecto. ¿Sigue siendo el correcto para el flujo completo, o necesita ajustes (más campos, otra fuente de datos)?

### Paso 2 — Añade el módulo de IA que faltaba

Si tu mini-proyecto no llegó a incluir un módulo de OpenAI (día 13), añádelo ahora: la clasificación, el resumen o el texto generado que tu brief describía.

### Paso 3 — Integra el contenido generado el día 18

Aquí está la pieza que hace "grande" al proyecto: conecta el insumo que preparaste ayer (texto, imagen, presentación) dentro del flujo de Make, de forma que se use automáticamente, no que lo pegues a mano cada vez.

<details>
<summary>Ejemplos de cómo integrarlo</summary>

- Si generaste una plantilla de texto con NotebookLM: que el módulo de OpenAI la use como base para personalizar cada respuesta
- Si generaste una imagen: que se adjunte automáticamente al email o mensaje que envía el flujo
- Si generaste una presentación con Gamma: que el flujo notifique cuándo está lista o la enlace en la respuesta automática

</details>

### Paso 4 — Añade la lógica condicional que le da inteligencia

Con un Router (día 12) o un Router basado en la respuesta de la IA (día 13), asegúrate de que tu flujo **decide**, no solo ejecuta siempre el mismo camino.

### Paso 5 — Blinda los puntos frágiles

Repasa el día 14: añade Retry a cualquier módulo que dependa de una IA o API externa, y un valor de Resume por defecto donde tenga sentido.

### Paso 6 — Prueba de principio a fin

Ejecuta el escenario completo con **Run once**, sin intervenir manualmente en ningún paso intermedio, y comprueba que el resultado final coincide con el "resultado esperado" de tu brief original.

---

## Ejercicio — Prueba de estrés de tu propio flujo

Antes de darlo por terminado, prueba tu escenario con **un caso límite**, no solo con el caso ideal: un dato vacío, un texto muy largo, una entrada ambigua que la IA pueda clasificar mal.

<details>
<summary>Qué hacer si algo se rompe</summary>

No es un fracaso — es exactamente para esto que existe el manejo de errores del día 14. Si el caso límite rompe tu flujo, ese es el momento de añadir el Retry, el Resume o el Router de fallback que le falte.

</details>

---

## Trabajo en equipo — Revisión cruzada

*(30 minutos)*

### El reto

En parejas (idealmente con alguien de un ámbito distinto al tuyo), enseñad vuestro proyecto grande al compañero como si fuera la primera vez que lo ve. La otra persona hace de "cliente exigente": pregunta qué pasa si el dato de entrada es raro, qué pasa si la IA falla, por qué elegiste ese trigger.

### Puesta en común

- ¿Qué pregunta del compañero os hizo ver un hueco en vuestro flujo que no habíais considerado?
- ¿Qué parte de vuestro proyecto os costó más explicar? Probablemente es la parte que también os costará más explicar mañana en la presentación.
- ¿Qué mejoraríais si tuvierais un día más?

---

## Lo que aprendiste hoy

- El proyecto grande no es un proyecto nuevo — es el mini-proyecto ampliado con contenido generado por IA y manejo de errores
- Integrar contenido generado por IA significa que el flujo lo use automáticamente, no que lo peguéis a mano
- Probar con un caso límite (no solo el caso ideal) es lo que revela si tu manejo de errores está completo
- Vuestro proyecto ya es una pieza de portfolio real: automatización + IA aplicada a un problema concreto de principio a fin
- Mañana lo presentáis — y con eso se cierra el curso

---

*Mañana: Presentación final — enseñáis vuestro mini-proyecto y proyecto grande al resto del grupo, y cerramos el curso.*
