# Software IV — Bitácoras de Clase y Documentación de Calidad

Repositorio académico correspondiente a la asignatura **Software IV** del programa de **Ingeniería de Sistemas**.

Este repositorio recopila y organiza el **seguimiento semanal de la asignatura** a través de una **bitácora digital por clase**, junto con el material, los talleres y las evidencias de cada sesión. El énfasis está en las **buenas prácticas de ingeniería de software, documentación, calidad y estrategias de evaluación de software**.

Cada carpeta `Clase#N/` guarda la presentación vista en clase, el material de apoyo y la bitácora diligenciada de esa semana.

---

## Objetivos

- Comprender y aplicar buenas prácticas en el desarrollo de software.
- Conocer la importancia de la documentación dentro del ciclo de vida de un software.
- Identificar y elaborar diferentes artefactos de software.
- Conocer estrategias y técnicas para evaluar la calidad de un software.
- Analizar diferentes características y atributos de calidad.
- Aplicar criterios de evaluación a proyectos de software.
- Fortalecer las prácticas de organización y documentación de proyectos.
- Consolidar los conocimientos adquiridos durante la asignatura.

---

## La bitácora digital

La bitácora es el registro individual de cada semana. Se diligencia sobre la plantilla
`Plantilla_Bitacora_Digital_Software4.docx` y está dividida en seis partes:

| Bloque | Qué se registra |
|---|---|
| **1. Información General** | Estudiante, código, semana, fecha, proyecto y rol |
| **A · 2.1 Resumen Teórico** | Los conceptos centrales de la sesión, con glosario y fórmulas |
| **A · 2.2 Tareas y Ejercicios** | Talleres y actividades de clase, con su entregable y evidencia |
| **B · Trabajo Independiente** | Desglose de horas T.I.E. (mínimo 4 horas por semana) |
| **C · Trazabilidad en Git** | Commits del repositorio que respaldan el trabajo realizado |
| **D · Autoevaluación** | Bloqueos encontrados, cómo se resolvieron y plan para la semana siguiente |

Al final se marca la lista de chequeo, la firma del estudiante y la fecha de subida.

---

## Registro de clases

| Carpeta | Fecha | Semana | Tema de la sesión |
|---|---|---|---|
| [`Clase#1/`](Clase%231/) | 05/08/2026 | Semana 3 | Calidad, Verificación y Validación, IEEE Std 1028-2008 |
| [`Clase#2/`](Clase%232/) | 12/08/2026 | Semana 4 | Los tipos de revisión del IEEE 1028 (exposiciones) |
| [`Clase#3/`](Clase%233/) | 19/08/2026 | Semana 5 | Estimación de software y Puntos de Función |
| [`Clase#4/`](Clase%234/) | 26/08/2026 | Semana 6 | Planificación de proyectos: EDT / WBS y Microsoft Planner |
| [`Clase#5/`](Clase%235/) | 02/09/2026 | Semana 7 | Pruebas de software: principios, ciclo de vida, tipos y niveles |

### Clase 1 — Calidad, Verificación y Validación (05/08/2026)

Sesión de apertura del curso. Se definió la **calidad** como el grado en que un proyecto
cumple los requisitos pactados, junto con las ideas de *gold plating* y análisis marginal.

El eje de la clase fue la diferencia entre **verificación** ("¿estamos construyendo el
producto correctamente?", no ejecuta código, usa revisiones e inspecciones) y
**validación** ("¿estamos construyendo el producto correcto?", sí ejecuta código y usa
pruebas de caja negra y caja blanca).

A partir de ahí se presentó el estándar **IEEE Std 1028-2008** y sus cinco tipos de
revisión: de Gestión, Técnicas, Inspecciones, Walk-throughs y Auditorías. Se profundizó
en la **Revisión Administrativa** (objetivos, entradas, salidas, los roles de Líder,
Registrador, Revisores y Responsables, y su procedimiento en tres momentos) y en la
**revisión entre pares**, con un tiempo límite de 60 minutos por sesión.

**Trabajo de la semana:** revisión entre pares del SRS de otro grupo con lista de chequeo,
y preparación de la exposición sobre el proceso de Inspección.

### Clase 2 — Tipos de revisión del IEEE 1028 (12/08/2026)

Sesión de **exposiciones por equipo**. Cada grupo presentó la definición, el proceso y el
instructivo de aplicación de uno de los métodos del estándar:

- **Revisiones Técnicas** — un equipo calificado evalúa si el producto es idóneo e
  identifica discrepancias frente a las especificaciones.
- **Inspecciones** — examen sistemático por pares dirigido por un **moderador imparcial**.
  Es el método más formal: usa criterios de entrada y salida, listas de chequeo, roles
  definidos y registro de defectos. *(Tema expuesto por mi equipo.)*
- **Walk-throughs** — análisis estático donde **el autor** guía al equipo por el producto
  y recibe preguntas y comentarios.
- **Auditorías** — examen **independiente**, hecho por un tercero externo, para verificar
  el cumplimiento de estándares, contratos y procedimientos.

La diferencia clave está en **quién dirige la sesión y para qué**: la inspección busca
defectos con un moderador imparcial, el walk-through busca retroalimentación y lo dirige
el autor, y la auditoría verifica cumplimiento desde afuera del equipo.

**Trabajo de la semana:** exposición de Inspecciones, clases interactivas en HTML sobre
los cuatro métodos y desarrollo de la prueba piloto IEEE 1028.

### Clase 3 — Estimación de software (19/08/2026)

La pregunta de la sesión fue **¿cuánto cuesta desarrollar software?**. Se revisó que el
costo no es solo el sueldo de los ingenieros: también entran hardware, viajes y
capacitación, seguros, alquiler y servicios, redes y recursos compartidos. Para llegar al
costo primero hay que estimar el **tamaño** y luego el **esfuerzo**.

Técnicas de estimación vistas:

- **Juicio experto puro** — rápido, pero la empresa depende de una sola persona.
- **Wideband Delphi** — estimación en grupo por rondas; suele ser mejor que la individual.
- **Analogía** — se compara con proyectos anteriores usando datos históricos.
- **PERT** — pondera tres escenarios: `e = (o + 4m + p) / 6`.
- **Puntos de Función (IFPUG)** — miden la funcionalidad desde el punto de vista del
  usuario, sin depender del lenguaje ni de la tecnología.

En Puntos de Función se trabajó el conteo de funciones de datos (**ILF**, **EIF**) y
transaccionales (**EI**, **EO**, **EQ**), los conceptos de **DET**, **RET** y **FTR**, las
matrices de complejidad (Baja / Media / Alta) y la tabla de pesos para obtener los
**puntos de función sin ajustar**. El ajuste final se hace valorando las 14
características generales del sistema:

```
Cpa = 0,65 + (0,01 × Cp)        PFa = PF × Cpa
```

**Trabajo de la semana:** estimación del proyecto integrador con Puntos de Función y una
segunda técnica, validada con una herramienta de IA como mecanismo de contraste.

### Clase 4 — Planificación de proyectos de software (26/08/2026)

La sesión tuvo dos partes. Primero las **exposiciones de los métodos de estimación** de
los compañeros, con evaluación entre pares de la exposición y del taller práctico
(Puntos de Función y Planning Poker / Puntos de Historia de Usuario).

Luego entró el tema nuevo: **cómo se planifica un proyecto**. Un proyecto es un esfuerzo
temporal para crear un producto o resultado único, con inicio y fin definidos y recursos
limitados; se sostiene sobre tres dimensiones —requisitos técnicos, aspectos humanos y
gestión—. Se compararon el modelo en cascada y los modelos incrementales (por incrementos
y por iteraciones) discutiendo cuál conviene según qué tan estables sean los requisitos,
y se repasaron los artefactos sugeridos en cada etapa del proyecto.

La herramienta central de la clase fue la **EDT / WBS (Estructura de Descomposición del
Trabajo)**, que baja el proyecto por niveles hasta hacerlo manejable:

```
Proyecto completo  →  Fases principales  →  Entregables por fase  →  Actividades
```

Esa estructura se lleva después a un tablero en **Microsoft Planner**, donde los *buckets*
representan las fases y cada tarea tiene responsable, fechas, etiquetas de prioridad y
lista de verificación. Dos reglas prácticas que quedaron de la sesión: una tarea debe
poder completarse en **1 a 5 días** (si no, se divide en subtareas) y conviene dejar un
**margen de seguridad del 10 % al 20 %** sobre la duración estimada.

La clase cerró con cuatro **casos de mitigación de riesgos** (fallas en la pasarela de
pagos, ausencia de un integrante clave, una vulnerabilidad de seguridad y un cambio tardío
de requisitos), decidiendo en cada uno la estrategia según su impacto en cronograma,
recursos, calidad y motivación del equipo.

**Trabajo de la semana:** planificación del proceso a entregar con su documentación
asociada, la EDT del proyecto y el tablero de seguimiento en Microsoft Planner.

### Clase 5 — Pruebas de software (02/09/2026)

La sesión repasó primero la diferencia entre **verificación y validación** y luego se
centró en las **pruebas de software**: qué son, para qué sirven y por qué importan tanto.
Para eso se revisaron varios casos reales de fallas costosas por no probar bien —el
cohete **Ariane 5**, la máquina de radioterapia **Therac-25**, el radar del misil
**Patriot** y el **Mars Climate Orbiter** de la NASA—, todos con pérdidas millonarias o
humanas por errores que unas pruebas adecuadas habrían detectado a tiempo.

Se vieron los **principios de la prueba de software** (se planifican desde antes del
desarrollo, les aplica el principio de Pareto, no son posibles las pruebas exhaustivas) y
el **ciclo de vida de las pruebas**: planificación, diseño, ejecución y cierre. Sobre la
clasificación, se compararon **caja negra, caja blanca y caja gris** según el
conocimiento del código, y se subió por la **pirámide de niveles de prueba** —unitarias,
integración, sistema y aceptación (con sus variantes alfa y beta)— cerrando con la
diferencia entre pruebas **funcionales** (el "qué" hace el sistema) y **no funcionales**
(el "cómo" lo hace).

En paralelo al tema teórico, el equipo avanzó en el aseguramiento de calidad del proyecto
integrador **SIGRA**: se consolidó el documento de entendimiento del problema con sus 22
requisitos funcionales, y se montó un ambiente local de **TestLink** con Docker para
empezar a diseñar los casos de prueba a partir de esos requisitos.

**Trabajo de la semana:** entendimiento del problema y requisitos funcionales de SIGRA,
instalación de TestLink y diseño de los primeros casos de prueba por módulo.

---

## Estructura del repositorio

```
BITACORAS DE CLASE/
├── Clase#1/
│   ├── Clase 5 de Agosto 2026.pdf              # presentación de la sesión
│   ├── Plantilla_Bitacora_Digital_Software4.docx   # bitácora semana 3
│   ├── Artefactos plantilla OneDrive/          # artefactos por fase del ciclo de vida
│   ├── SIGRA TRABAJO EQUIPO/                   # material de la exposición de Inspecciones
│   └── Tarea1/                                 # revisión entre pares del SRS
├── Clase#2/
│   ├── Clase 12 de Agosto 2026.pdf
│   ├── Plantilla_Bitacora_Digital_Software4.docx   # bitácora semana 4
│   ├── Presentacion_Inspecciones_IEEE_1028_UCO_final.pptx
│   ├── Prueba piloto IEEE 1028 — Calificar e imprimir.pdf
│   └── Clases_Interactivas_IEEE1028_FINAL_4_VERSIONES/
├── Clase#3/
│   ├── Clase 19 de agosto 2026.pdf
│   ├── Plantilla_Bitacora_Digital_Software4.docx   # bitácora semana 5
│   └── Clase_Interactiva_Estimacion_Software_v3.html
├── Clase#4/
│   ├── Clase 26 Agosto 2026.pdf
│   ├── Plantilla_Bitacora_Digital_Software4.docx   # bitácora semana 6
│   ├── Curso_ INGENIERIA Camilo.pdf                # evaluación entre pares
│   └── Curso_ INGENIERIA Arbelaez.pdf              # evaluación entre pares
├── Clase#5/
│   ├── Clase 2 Septiembre 2026.pdf
│   ├── Plantilla_Bitacora_Digital_Software4.docx   # bitácora semana 7
│   ├── Calificacion_a_Ivan Daniel Naranjo Botero.pdf   # evaluación entre pares
│   ├── Calificacion_a_Jean Paul Ortiz Restrepo.pdf     # evaluación entre pares
│   ├── requisitos_funcionales/                     # problema y RF-01 a RF-22 de SIGRA
│   └── testlink-sigra/                             # guía Docker para TestLink
└── README.md
```

---

## Trazabilidad en Git

El historial del repositorio funciona como **evidencia del trabajo independiente**. Por
cada clase se hacen dos commits, siempre en el mismo orden:

1. `docs(claseN): agregar material de la sesion del DD/MM/AAAA ...` — el PDF de la clase,
   talleres y evidencias.
2. `docs(claseN): diligenciar bitacora digital de la semana N (DD/MM/AAAA)` — la bitácora.

De esa forma los hashes que aparecen en el **Bloque C** de cada bitácora corresponden a
commits que ya existen y se pueden abrir directamente en GitHub.

---

## Datos del estudiante

- **Estudiante:** Andres Felipe Velez Alcaraz
- **Código:** 1017245136
- **Programa:** Ingeniería de Sistemas — 9° semestre
- **Asignatura:** Software IV
- **GitHub:** [@andrias01](https://github.com/andrias01)
