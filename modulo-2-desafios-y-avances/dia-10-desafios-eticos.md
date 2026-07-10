# Día 10 — Desafíos éticos: sesgos, privacidad y derechos de autor

**Módulo 2 · Desafíos y Avances en Inteligencia Artificial**

---

## Recapitulando el día anterior

Rápido:

> **¿Cuál es la diferencia clave entre un chatbot y un agente?**

Si la recuerdas sin mirar, estás listo. Si no, echa un vistazo al día 9 antes de continuar.

---

## De lo que la IA puede hacer a lo que debería hacer

Llevas nueve días viendo lo que la IA es capaz de generar y automatizar. Hoy cambiamos de pregunta: no "qué puede hacer", sino **qué riesgos trae consigo** y qué deberías tener en cuenta antes de usarla en tu trabajo. Tres bloques: sesgos, privacidad y derechos de autor.

Esto no es teoría abstracta — son decisiones prácticas que vas a tomar la próxima vez que pegues un dato de un cliente en ChatGPT o generes una imagen para un proyecto comercial.

---

## Sesgos algorítmicos

Un modelo de IA aprende de datos que existen en el mundo real — y el mundo real tiene sesgos históricos (de género, raza, edad, clase social). El modelo no los inventa, **los hereda y a veces los amplifica**.

### Ejemplos conocidos

- Herramientas de selección de personal entrenadas con currículums históricos que penalizaban a mujeres, porque el histórico de contrataciones ya era mayoritariamente masculino.
- Generadores de imágenes que, al pedir "un CEO" o "un médico", producen mayoritariamente hombres blancos; al pedir "una secretaria" o "un cuidador", producen mayoritariamente mujeres.

### Por qué te importa aunque no programes

Si usas IA para preseleccionar candidatos, redactar ofertas de trabajo, generar imágenes de marketing o tomar decisiones que afectan a personas, **el sesgo del modelo se convierte en el sesgo de tu decisión** — aunque tú no tuvieras intención de discriminar a nadie.

**Lo que puedes hacer:** revisar los resultados con ojo crítico, especialmente en decisiones que afectan a personas (contratación, crédito, admisión), y no asumir que un resultado es "neutral" solo porque lo generó una máquina.

---

## Privacidad

Cada vez que escribes algo en ChatGPT, Gemini o cualquier IA, esa información sale de tu equipo y llega a un servidor de la empresa que la opera. Qué pasa después depende de la configuración:

| Situación | Riesgo |
|---|---|
| Tienes activado "mejorar el modelo con tus conversaciones" | Tus datos pueden usarse para entrenar futuras versiones del modelo |
| Pegas datos de un cliente (nombre, email, historial médico, contrato) | Esos datos salen de tu control y de los sistemas de tu empresa |
| Usas una IA gratuita para procesar documentos internos | Puede que las condiciones del servicio gratuito sean menos estrictas que las de un plan empresarial |

### Buenas prácticas

- Revisa la configuración de privacidad de la herramienta que uses (en ChatGPT: *Configuración → Datos → Mejora del modelo para todos*).
- Nunca pegues datos personales sensibles de terceros (clientes, pacientes, empleados) en una IA gratuita sin verificar antes las condiciones de uso.
- Si tu empresa maneja datos sensibles, comprueba si existe un plan empresarial con garantías distintas (muchas herramientas no entrenan con los datos de cuentas de empresa).

---

## Derechos de autor

Aquí hay dos preguntas separadas, y conviene no mezclarlas:

**1. ¿Con qué se entrenó el modelo?**
Muchos modelos de imagen, texto y vídeo se entrenaron con contenido protegido por derechos de autor (obras de artistas, artículos, fotografías) sin permiso explícito de sus autores. Esto ha generado demandas activas contra varias empresas de IA, y no hay todavía una respuesta legal definitiva y global.

**2. ¿De quién es el contenido que genera la IA?**
Depende del país y de la herramienta: en algunos países, el contenido generado únicamente por IA sin intervención humana creativa suficiente puede no ser protegible por derechos de autor — cualquiera podría reutilizarlo, incluida tu competencia. Cada herramienta tiene además sus propias condiciones de uso comercial.

**En la práctica:** antes de usar contenido de IA en algo comercial (un logo, una campaña), comprueba las condiciones de uso de la herramienta concreta que usaste — no todas ofrecen las mismas garantías.

---

## Ejercicio 1 — Detecta el sesgo

Genera imágenes con estos cuatro prompts exactos, sin más detalles, en la herramienta que prefieras: *"un CEO"*, *"una enfermera"*, *"un ingeniero"*, *"una niñera"*. Observa el patrón de género, edad y raza que se repite.

<details>
<summary>Qué observar</summary>

- ¿Se repite el mismo perfil demográfico en cada rol sin que lo hayas pedido?
- ¿Qué pasa si añades explícitamente "diverso" o especificas género/edad? ¿Cambia el resultado?
- Esto no es un fallo técnico puntual — es un reflejo del contenido con el que se entrenó el modelo.

</details>

---

## Ejercicio 2 — Auditoría de privacidad de 5 minutos

Entra en la configuración de privacidad de la IA que más uses (ChatGPT, Gemini, Copilot...) y comprueba:

- ¿Está activada la opción de usar tus conversaciones para entrenar el modelo?
- ¿Sabes dónde consultar o borrar tu historial?
- Piensa en la última vez que usaste la IA para trabajo: ¿pegaste algún dato que no deberías haber compartido?

---

## Trabajo en equipo — El comité de ética

*(30 minutos)*

### El reto

Vuestra empresa quiere lanzar una campaña de marketing usando exclusivamente contenido generado por IA (imágenes, textos y un vídeo corto). El equipo directivo os pide una recomendación.

Cada equipo representa un rol distinto y debe defender su postura ante el resto:

| Equipo | Rol |
|---|---|
| **Equipo 1** | Dirección de marketing — quiere lanzar ya, rapidez y ahorro de costes |
| **Equipo 2** | Legal — preocupado por derechos de autor y uso comercial |
| **Equipo 3** | Un artista/diseñador freelance afectado por la sustitución de su trabajo |
| **Equipo 4** | Responsable de protección de datos — preocupado por qué información se ha compartido con las herramientas usadas |

### Debate

Cada equipo expone su postura en 3-4 minutos. Al final, el grupo entero vota una recomendación conjunta: ¿lanzar la campaña tal cual, lanzarla con condiciones, o no lanzarla?

Reflexión final: ¿ha cambiado tu opinión inicial después de escuchar los otros roles?

---

## Lo que aprendiste hoy

- Los modelos de IA heredan los sesgos de los datos con los que se entrenaron — no son neutrales por defecto
- Cualquier dato que escribes en una IA puede usarse para entrenarla si no revisas la configuración de privacidad
- Nunca compartas datos sensibles de terceros en una herramienta gratuita sin comprobar antes sus condiciones
- El contenido generado por IA plantea dos problemas de derechos de autor distintos: con qué se entrenó el modelo, y de quién es lo que genera
- Antes de usar contenido de IA en algo comercial, revisa las condiciones de uso específicas de esa herramienta

---

*Mañana: Desafíos sociales — deepfakes, regulación y la Ley de IA de la UE.*
