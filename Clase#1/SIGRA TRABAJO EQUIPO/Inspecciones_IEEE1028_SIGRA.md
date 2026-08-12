# Análisis e Instructivo de Inspecciones de Software: Estándar IEEE Std 1028-2008 y su Aplicación en SIGRA

**Asignatura:** Ingeniería de Software / Calidad de Software  
**Proyecto:** Software Integral de Gestión de Resultados de Aprendizaje (SIGRA)  
**Documentos de Referencia:**  
- *IEEE Std 1028-2008: IEEE Standard for Software Reviews and Audits* (`dokumen.pub_ieee-std-1028-2008...pdf`)
- *Especificación de Requisitos de Software (SRS) - SIGRA* (`SIGRA.pdf`)

---

## Pregunta 1: Definición de Inspecciones según IEEE Std 1028-2008 y su Relación con SIGRA

### 1.1 Definición Formal según la Estandarización
De acuerdo con el estándar **IEEE Std 1028-2008** (Cláusula 3.3 y Cláusula 6.1):

> **Inspección (Inspection):** Es un examen visual, formal y sistemático realizado por un equipo de pares (*peer examination*) sobre un producto de software con el objetivo principal de **detectar e identificar anomalías** (errores, omisiones, inconsistencias y desviaciones respecto a los estándares, regulaciones y especificaciones técnicas).

Las inspecciones se caracterizan por las siguientes propiedades fundamentales fijadas por el estándar:
1. **Liderazgo Imparcial:** Es guiada por un facilitador capacitado e imparcial (*Inspection Leader*), quien no es el autor del producto.
2. **Roles Definidos:** Participa un equipo de **3 a 6 integrantes** con responsabilidades estrictas (Líder, Autor, Lector, Registrador e Inspectores con perspectivas específicas).
3. **Restricción Gerencial:** La gerencia (*management*) **no debe participar** en las sesiones de inspección para garantizar un entorno libre de presiones y evitar la evaluación del desempeño individual de los desarrolladores.
4. **Obligatoriedad de Recolección de Datos y Mejora (Cláusula 6.8 y 6.9):** La recolección de métricas de esfuerzo y anomalías, así como el uso de estos datos para la mejora continua del proceso de desarrollo y de las listas de chequeo (*checklists*), es un elemento **mandatorio y exclusivo** de las inspecciones (a diferencia de otros tipos de revisión como las *walk-throughs*).

#### Objetivos Clave de la Inspección (IEEE 1028 - Cláusula 6.1):
- Verificar que el producto de software cumple exactamente con sus especificaciones.
- Verificar que satisface los atributos de calidad especificados (seguridad, fiabilidad, mantenibilidad, etc.).
- Comprobar la conformidad con normas, guías, planes y procedimientos aplicables.
- Identificar desviaciones y registrar anomalías para su posterior corrección (*rework*).
- Recolectar datos cuantitativos de ingeniería de software para optimizar el proceso de desarrollo.

---

### 1.2 Relación con el Proyecto SIGRA

El proyecto **SIGRA (Software Integral de Gestión de Resultados de Aprendizaje)** presenta una relación bidireccional con el concepto de Inspección:

#### A) Aplicación de Inspecciones durante la Construcción de SIGRA (Verificación del Software)
SIGRA es un producto web responsive desarrollado bajo arquitectura Java (Backend), Angular (Frontend) y PostgreSQL (Base de Datos), cuyo levantamiento de requisitos adopta la norma IEEE 830 (según Sección 2.4 de `SIGRA.pdf`). 

La técnica de **Inspección de IEEE 1028** se relaciona directamente con la calidad de SIGRA mediante la evaluación rigurosa de sus artefactos de software:
- **Inspección de Requisitos:** Inspeccionar la SRS de SIGRA (`SIGRA.pdf`) para asegurar la trazabilidad, completitud y ausencia de ambigüedades en sus 22 Requisitos Funcionales (RF-01 a RF-22) y Requisitos No Funcionales (RNF-01 a RNF-20).
- **Inspección de Código Fuente y Diseño:** Inspeccionar las clases Java del backend y los componentes Angular frente a reglas de seguridad críticas como el hashing de contraseñas con sal (RNF-10), sanitización contra inyección SQL (RNF-14), expiración del token JWT a los 60 minutos (RNF-15) y control de acceso RBAC (RF-05).
- **Inspección del Modelo de Datos:** Validar que la base de datos implemente la eliminación lógica de registros (*soft delete*) exigida por RF-19 y RNF-16 para mantener el historial inalterable con fines de auditoría.

#### B) Paralelismo Conceptual: El Modelo de Calidad de SIGRA como un Sistema de Inspección Académica
Existe una analogía directa entre la filosofía de inspecciones de IEEE 1028 y las funcionalidades del dominio de negocio de SIGRA:
- En IEEE 1028, se examina un producto, se detectan anomalías y se aplican acciones correctivas para mejorar la calidad.
- En SIGRA, los profesores evalúan los **Resultados de Aprendizaje (RA)**, clasifican el nivel de logro de los estudiantes (Bajo, Medio, Alto, Sobresaliente - RF-14), detectan deficiencias académicas (si >40% obtiene nivel Bajo/Medio - RF-16) y formulan **Acciones de Mejora** (RF-17), las cuales luego se convierten en **nuevas evaluaciones de refuerzo** (RF-18), cerrando un ciclo continuo de evaluación y mejora.

---

## Pregunta 2: Descripción del Proceso según la Estandarización y como se ve en SIGRA

### 2.1 Proceso Estándar de Inspección según IEEE Std 1028-2008 (Cláusula 6.5)

El proceso de inspección definido por la norma se divide en **7 etapas secuenciales estrictas**:

```
[1. Preparación Gerencial] ──> [2. Planificación] ──> [3. Visión General / Overview]
                                                                  │
[6. Retrabajo / Rework] <── [5. Reunión de Examen] <── [4. Preparación Individual]
         │
         └──> [7. Seguimiento y Cierre] ──> [8. Recolección de Datos y Mejora]
```

#### Detalles de cada fase (IEEE 1028):
1. **Preparación de la Administración (6.5.1):** La gerencia aprueba el tiempo y recursos necesarios, provee la infraestructura, garantiza la capacitación del personal y se compromete a actuar sobre las recomendaciones del equipo.
2. **Planificación de la Inspección (6.5.2):** El autor entrega los materiales al Líder de Inspección. El Líder:
   - Selecciona el equipo de 3 a 6 integrantes.
   - Asigna los roles (Líder, Autor, Lector, Registrador, Inspectores).
   - Establece la tasa de inspección recomendada (ej. 2 a 3 páginas por hora para requisitos; 100 a 200 líneas de código por hora para código fuente - Tabla 6.5.2).
   - Fija fechas, distribuye materiales y especifica el alcance.
3. **Visión General / Overview (6.5.3 y 6.5.4):** Sesión introductoria opcional pero recomendada donde el autor presenta una visión general del producto al equipo y el líder explica las reglas del juego.
4. **Preparación Individual (6.5.5):** Cada miembro inspecciona el producto de forma autónoma utilizando listas de chequeo (*checklists*). Anota las anomalías detectadas, registra su tiempo individual de preparación y envía los hallazgos preliminares al líder.
5. **Reunión de Examen / Inspección (6.5.6):**
   - *Introducción (6.5.6.1):* El líder inicia la sesión recordando que el objetivo es **detectar anomalías, no resolverlas**, y criticar el producto, nunca al autor.
   - *Lectura y Detección (6.5.6.3):* El Lector guía la revisión leyendo o parafraseando el producto en fragmentos pequeños (1 a 3 líneas o secciones lógicas). Los inspectores exponen sus hallazgos.
   - *Registro (6.5.6.3):* El Registrador anota cada anomalía en la Lista de Anomalías con su ubicación, descripción exacta y clasificación según IEEE Std 1044-1993 (Faltante, Incorrecto, Ambiguo, Inconsistente, Riesgoso, etc.).
   - *Decisión de Salida / Exit Decision (6.5.6.5):* Al final de la reunión, el equipo determina la disposición del producto entre tres opciones:
     - **Aceptar sin verificación o con verificación menor:** El producto se aprueba inmediatamente o requiere correcciones menores.
     - **Aceptar previa verificación de retrabajo (Rework Verification):** Se aprueba solo después de que el líder u otro miembro verifique que el autor corrigió las anomalías.
     - **Re-inspeccionar (Reinspect):** El producto se rechaza debido al volumen o severidad de anomalías. Se exige un nuevo ciclo completo de inspección tras el retrabajo.
6. **Retrabajo y Seguimiento / Rework & Follow-up (6.5.7):** El autor corrige las anomalías. El líder de inspección verifica que todas las correcciones se hayan realizado correctamente y que no se hayan introducido nuevos errores.
7. **Recolección de Datos y Mejora del Proceso (6.8 y 6.9):** Se compilan las métricas del proceso (tiempos de preparación, tasas de inspección, cantidad y clasificación de anomalías por severidad: Catastrófica, Crítica, Marginal, Despreciable) para actualizar las listas de chequeo y mejorar los procesos de desarrollo.

---

### 2.2 Roles en el Proceso de Inspección (IEEE 1028 - Cláusula 6.2)

| Rol | Responsabilidades según IEEE 1028 | Asignación sugerida en el Equipo SIGRA |
| :--- | :--- | :--- |
| **Inspection Leader (Líder)** | Planifica la inspección, asigna roles, modera la reunión, asegura la recolección de datos y verifica el retrabajo. **No puede ser el autor**. | Simón Tabares Arias / Andrés Felipe Vélez |
| **Author (Autor)** | Proporciona el producto y documentos base, resuelve dudas puntuales durante la sesión y ejecuta el retrabajo (*rework*). **No puede ser Líder, Lector ni Registrador**. | Juan Camilo Bernal Carmona (Backend/Arq) |
| **Reader (Lector)** | Guía al equipo a través del producto, parafraseando secciones y manteniendo la reunión en un flujo estructurado. | Santiago Torres Castaño / Jean Paul Ortiz |
| **Recorder (Registrador)** | Registra oficialmente cada anomalía, ubicación, tipo y severidad en la lista de hallazgos. | Juan José Narváez Marín / José Alejandro |
| **Inspectors (Inspectores)** | Revisan el producto desde perspectivas específicas (Seguridad, Rendimiento, Requisitos, Usabilidad, Pruebas) e identifican anomalías. | Todo el equipo evaluador |

---

### 2.3 Cómo se refleja y aplica en el Software SIGRA

La aplicación del proceso de inspección al software **SIGRA** se manifiesta en dos niveles:

#### 1. Inspección sobre la Especificación de Requisitos y Código de SIGRA
Durante la fase de construcción de SIGRA, el proceso de inspección de IEEE 1028 se aplica directamente a sus módulos:
- **En la Requisición (SRS):** Se evalúa la coherencia de las reglas de negocio de SIGRA (ej. verificar que cada asignatura tenga obligatoriamente entre 5 y 7 RAs según RF-03 y RF-06).
- **En la Autenticación y Seguridad (RF-04, RNF-10, RNF-12, RNF-15):** Se inspeccionan las funciones Java para certificar que el hash utilice sal, que el JWT expire strictly a los 60 minutos y que el bloqueo tras 5 intentos fallidos consecutivos funcione sin revelar cuál credencial falló.
- **En la Evaluación y Niveles de Logro (RF-11, RF-12, RF-14):** Se verifica por inspección de código que la suma de porcentajes de evaluaciones activas por RA no exceda el 100%, que las notas estén acotadas entre 0.0 y 5.0, y que el nivel de logro clasifique correctamente los rangos (Bajo: 0.0-2.9, Medio: 3.0-3.9, Alto: 4.0-4.5, Sobresaliente: 4.6-5.0).
- **En la Trazabilidad y Auditoría (RF-13, RF-19, RNF-16):** Se inspecciona que cualquier calificación registrada fuera de la fecha tentativa se marque visualmente y que toda acción (creación, modificación, inactivación) guarde registro en la tabla de auditoría con usuario, fecha, hora, acción y resultado.

#### 2. Trazabilidad del Retrabajo en SIGRA
Así como el estándar exige la verificación del *rework*, el sistema SIGRA almacena una traza completa e inalterable de modificaciones mediante eliminación lógica (*soft delete*) y tablas de auditoría, garantizando la trazabilidad histórica exigida tanto en la ingeniería de software como en la gestión de calidad académica.

---

## Pregunta 3: Instructivo de cómo aplicar el método según la estandarización y cómo hacerlo en SIGRA

A continuación se presenta una guía paso a paso operativa dividida en dos partes: el **Instructivo Genérico según IEEE Std 1028-2008** y la **Guía Práctica Aplicada al Proyecto SIGRA**.

---

### 3.1 Instructivo General de Aplicación del Método de Inspección (IEEE 1028-2008)

#### Paso 1: Verificación de Criterios de Entrada (Entry Criteria)
Antes de convocar a una inspección, el Líder de Inspección debe validar:
- [ ] El producto de software a inspeccionar está completo y libre de errores sintácticos o de formato básicos (se pasaron linters, compiladores y correctores).
- [ ] Se cuenta con la especificación o documento fuente de referencia (SRS, estándar de codificación, etc.).
- [ ] La gerencia ha autorizado los tiempos y recursos.

#### Paso 2: Conformación del Equipo y Asignación de Roles
- Designar un **Líder de Inspección** (capacitado, imparcial).
- Identificar al **Autor** del producto.
- Asignar el rol de **Lector** y **Registrador**.
- Asignar **Inspectores** asignándoles enfoques temáticos específicos (ej. Inspector 1: Seguridad; Inspector 2: Cumplimiento de SRS; Inspector 3: Manejo de Errores y Excepciones).

#### Paso 3: Planificación y Entrega del Paquete de Inspección
- El Líder calcula el tamaño del material y determina las sesiones necesarias respetando la tasa recomendada:
  - *Documentos de Requisitos / Arquitectura:* 2 a 3 páginas por hora (PPH).
  - *Código Fuente:* 100 a 200 líneas de código por hora (LPH).
- Se envía el paquete a los participantes con mínimo 48 horas de anticipación:
  1. Producto de software a inspeccionar.
  2. Documento de especificación/requisitos fuente.
  3. Lista de Chequeo (*Checklist*) temática.
  4. Formulario de registro preliminar de anomalías.

#### Paso 4: Preparación Individual (Trabajo Autónomo)
- Cada inspector estudia el material línea por línea o sección por sección.
- Aplica la lista de chequeo y registra anomalías encontradas en su plantilla individual.
- Registra el tiempo exacto invertido en la preparación.
- Envía su reporte al Líder antes de la reunión. Si los participantes no se prepararon adecuadamente, el Líder cancela o reprograma la sesión.

#### Paso 5: Ejecución de la Reunión de Inspección (Máximo 2 horas por sesión)
1. **Apertura (5 min):** El Líder presenta los roles, la agenda y reafirma la regla: *"Buscamos anomalías en el producto, no culpables. No se discuten soluciones durante el examen"*.
2. **Revisión de Ítems Generales (10 min):** Se registran anomalías globales del producto.
3. **Examen Detallado (60-80 min):**
   - El Lector presenta y parafrasea el producto en fragmentos pequeños.
   - Los inspectores reportan las anomalías halladas.
   - El Registrador anota cada hallazgo en la **Lista Oficial de Anomalías**:
     - *ID de Anomalía*
     - *Ubicación exacta (Archivo, línea, sección)*
     - *Descripción del problema*
     - *Categoría (Según IEEE 1044: Faltante, Incorrecto, Ambiguo, Inconsistente, etc.)*
     - *Severidad: Catastrófica, Crítica, Marginal o Despreciable*.
4. **Consolidación de la Lista (10 min):** El Líder repasa la lista con el equipo para garantizar claridad y consenso en la redacción.
5. **Decisión de Salida (Exit Decision - 5 min):** El equipo vota la disposición del producto:
   - *Aceptado* | *Aceptado con verificación de retrabajo* | *Re-inspección requerida*.

#### Paso 6: Retrabajo (Rework)
- El Autor recibe la Lista Oficial de Anomalías y corrige cada punto en el producto de software.

#### Paso 7: Seguimiento, Verificación y Cierre (Follow-up)
- El Líder de Inspección (o la persona asignada) revisa que cada anomalía registrada haya sido resuelta adecuadamente y que las modificaciones no hayan afectado otras áreas.
- Se firma el cierre de la inspección.

#### Paso 8: Registro de Métricas e Historias de Mejora
- Se archiva el Informe de Inspección con los datos de tiempo de preparación, tiempo de reunión, volumen inspeccionado y métricas de anomalías para enriquecer las listas de chequeo futuras.

---

### 3.2 Instructivo Práctico Aplicado a SIGRA
**Caso de Estudio Práctico:** Inspección de la Implementación del Módulo de *"Cálculo y Clasificación del Nivel de Logro, Estadísticas y Generación de Conclusiones"* (Requisitos **RF-14, RF-15, RF-16** en `SIGRA.pdf`).

#### Paso 1: Insumos y Criterios de Entrada para la Inspección en SIGRA
- **Producto a Inspeccionar:** Clase Java `AchievementService.java` y componente Angular `achievement-report.component.ts`.
- **Documento Fuente:** Especificación de Requisitos de Software `SIGRA.pdf` (Páginas 24 y 25, numerales 3.2.14, 3.2.15 y 3.2.16).
- **Lista de Chequeo:** Checklist de Cumplimiento de Reglas de Negocio y Calidad de Código de SIGRA.

#### Paso 2: Equipo de Inspección Asignado
- **Líder de Inspección:** Simón Tabares Arias (Verifica proceso y seguimiento).
- **Autor del Código:** Juan Camilo Bernal Carmona (Project Manager / Backend).
- **Lector:** Santiago Torres Castaño (Guía el recorrido del código Java/Angular).
- **Registrador:** Andrés Felipe Vélez Alcaraz (Documenta anomalías y tiempos).
- **Inspectores:**
  - *Inspector 1 (Seguridad/Robustez):* Jean Paul Ortiz Restrepo (Verifica RNF-10, RNF-14 SQL Injection y RNF-15 JWT).
  - *Inspector 2 (Reglas de Negocio y Lógica):* Juan José Narváez Marín (Verifica rangos de RF-14, regla del >40% de RF-16 y mensaje "sin datos suficientes" de RF-15).

#### Paso 3: Lista de Chequeo (Checklist) Específica para la Inspección de SIGRA

```markdown
### Checklist de Inspección - Módulo de Niveles de Logro y Conclusiones (SIGRA)

1. [ ] **Clasificación de Nivel de Logro (RF-14):**
   - ¿El código clasifica `0.0 a 2.9` como "bajo"?
   - ¿El código clasifica `3.0 a 3.9` como "medio"?
   - ¿El código clasifica `4.0 a 4.5` como "alto"?
   - ¿El código clasifica `4.6 a 5.0` como "sobresaliente"?
   - ¿Qué sucede si la nota ingresada está fuera del rango 0.0-5.0? (Debe rechazarla según RF-12).

2. [ ] **Estadísticas Descriptivas (RF-15):**
   - ¿Se calculan promedios y distribuciones por evaluación, RA, asignatura y semestre?
   - Si NO existen calificaciones registradas, ¿el sistema retorna explícitamente "sin datos suficientes para calcular" en lugar de `null`, `0` o un valor vacío?

3. [ ] **Regla de Generación de Conclusiones (RF-16):**
   - ¿El sistema evalúa si MÁS del 40% de los estudiantes obtiene nivel "bajo" o "medio" en un RA?
   - Si se supera el 40%, ¿genera exactamente la conclusión: `"Nivel de logro insuficiente en [RA]: se recomienda registrar una acción de mejora"`?
   - En caso contrario, ¿muestra el mensaje de desempeño satisfactorio?
   - ¿El módulo realiza este cálculo mediante agregaciones convencionales SIN uso de Inteligencia Artificial (cumpliendo Restricción 2.4 y RNF-15 de `SIGRA.pdf`)?

4. [ ] **Seguridad y Control de Acceso (RF-05, RNF-14):**
   - ¿La consulta a la base de datos utiliza consultas parametrizadas u ORM (evitando SQL Injection)?
   - Si un usuario con rol "Estudiante" intenta invocar el endpoint de generación de conclusiones, ¿el servidor retorna HTTP 403 Forbidden?
```

#### Paso 4: Simulación de la Sesión de Inspección y Registro de Hallazgos

Durante la sesión de inspección conducida por Santiago Torres (Lector) y moderada por Simón Tabares (Líder), los inspectores identifican las siguientes anomalías en el código de SIGRA:

##### Formulario de Registro de Anomalías de Inspección (Ejemplo de Ejecución)

| ID | Ubicación | Descripción de la Anomalía | Categoría (IEEE 1044) | Severidad | Disposición / Retrabajo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **ANO-SIG-01** | `AchievementService.java` Línea 45 | En el cálculo del nivel de logro (RF-14), el código usa `<=` 4.5 para "alto", provocando que una nota de `4.55` se clasifique como "alto" en vez de "sobresaliente" (4.6-5.0). | Incorrecto / Lógica | **Crítica** | Juan Camilo debe ajustar los operadores de comparación de los rangos acotados. |
| **ANO-SIG-02** | `AchievementService.java` Línea 88 | Al calcular estadísticas sin notas (RF-15), el método retorna `Double.NaN` en lugar de la cadena textual `"sin datos suficientes para calcular"`. | Faltante / Especificación | **Marginal** | Modificar el DTO de respuesta para retornar el mensaje textual requerido por la SRS. |
| **ANO-SIG-03** | `AchievementController.java` Línea 30 | El endpoint no valida el rol del usuario (RF-05), permitiendo que un Estudiante consulte conclusiones generales de la materia. | No conforme a estándar / Seguridad | **Crítica** | Añadir la anotación `@PreAuthorize("hasAnyRole('PROFESOR', 'ADMIN')")`. |

#### Paso 5: Decisión de Salida y Retrabajo en SIGRA
- **Decisión del Equipo:** **Aceptar previa verificación de retrabajo (Rework Verification)**.
- **Acción:** Juan Camilo Bernal realiza las correcciones en el Backend de SIGRA.
- **Verificación:** Simón Tabares (Líder) revisa el commit del backend, ejecuta la suite de pruebas unitarias (RNF-20) y comprueba que las 3 anomalías hayan sido solucionadas sin romper otros módulos.

#### Paso 6: Cierre, Trazabilidad e Historial en SIGRA
- El informe de inspección se guarda en el repositorio del proyecto.
- Los cambios integrados quedan respaldados por el historial de auditoría de SIGRA (RF-19 y RNF-16), asegurando la trazabilidad exigida por el estándar de calidad.

---

## Conclusión y Cuadro Comparativo Resumen

| Criterio | Estándar IEEE Std 1028-2008 (Inspecciones) | Aplicación en el Proyecto SIGRA |
| :--- | :--- | :--- |
| **Objetivo Principal** | Detección formal de anomalías y recolección de métricas de calidad. | Garantizar que el software SIGRA cumpla con sus 22 RF y RNFs sin fallos de seguridad ni errores de cálculo. |
| **Grado de Formalidad** | Muy alto (el segundo más formal después de las Auditorías). | Riguroso sobre los artefactos críticos: SRS, Módulo de Autenticación, Niveles de Logro y Auditoría. |
| **Participación Gerencial** | **Prohibida** en la sesión de inspección. | Los roles administrativos participan en el software SIGRA como usuarios del sistema, pero NO en las inspecciones de código. |
| **Métricas y Mejora** | **Mandatorio** recolectar datos de anomalías y esfuerzo para mejorar el proceso (Cláusula 6.8 y 6.9). | Los hallazgos alimentan la mejora continua del desarrollo de SIGRA y se reflejan en la trazabilidad del sistema. |
