# Guía Explicativa del Proceso de Inspección de Software (Estándar IEEE Std 1028-2008)

**Asignatura:** Ingeniería de Software / Calidad de Software  
**Estándar de Referencia:** *IEEE Std 1028-2008: IEEE Standard for Software Reviews and Audits* (Cláusula 6: *Inspections*)  
**Propósito:** Guía práctica y didáctica para comprender y aplicar la técnica formal de Inspecciones de Software.

---

## 1. Definición de Inspección según IEEE Std 1028-2008

### 1.1 ¿Qué es una Inspección de Software?
De acuerdo con el estándar **IEEE Std 1028-2008 (Cláusula 3.3 y 6.1)**:

> **Inspección (Inspection):** Es un examen visual, formal y riguroso realizado por un equipo de pares (*peer review*) sobre un artefacto de software (requisitos, arquitectura, diseño, código fuente, planes de prueba) con el objetivo primario de **detectar e identificar anomalías** (errores, inconsistencias, omisiones y desviaciones respecto a los estándares).

Es considerada una de las técnicas **más rigurosas y formales** de la ingeniería de software (solo superada por las auditorías).

---

### 1.2 Reglas e Identificadores Fundamentales del Método
Para que una revisión se considere una **Inspección IEEE 1028**, debe cumplir obligatoriamente con 5 principios:

1. **Liderazgo Imparcial:** Es coordinada por un **Líder de Inspección** (*Inspection Leader*) capacitado, quien **no puede ser el autor** del producto.
2. **Roles Estructurados:** Participa un equipo multidisciplinario de **3 a 6 integrantes**, cada uno con responsabilidades explícitas (Líder, Autor, Lector, Registrador e Inspectores).
3. **Sin Participación Gerencial:** La gerencia o administración **no participa en las sesiones**. Esto evita que la inspección se use para evaluar el desempeño del desarrollador y garantiza que el foco permanezca exclusivamente en la calidad del producto.
4. **Listas de Chequeo (*Checklists*):** Es obligatorio el uso de guías y listas de chequeo preparadas previamente según el tipo de artefacto (requisitos, código, seguridad, etc.).
5. **Recolección Mandatoria de Datos y Métricas (Cláusula 6.8 y 6.9):** Se deben registrar métricas cuantitativas (tiempo de preparación, tasa de lectura, cantidad y severidad de anomalías encontradas). Esto alimenta el proceso de mejora continua del equipo.

---

### 1.3 Objetivos Principales de una Inspección
* **Verificar la calidad del producto:** Comprobar que cumple con los requisitos y las especificaciones de entrada.
* **Garantizar la conformidad con estándares:** Asegurar que respete las normas de arquitectura, estilo de código y normativas legales o de seguridad.
* **Detección temprana de errores:** Encontrar fallos en etapas iniciales (como requisitos o diseño), lo cual cuesta hasta 100 veces menos que corregirlos en producción.
* **Mejora continua del proceso:** Utilizar los datos recolectados para perfeccionar las listas de chequeo y evitar la repetición de los mismos errores en futuros proyectos.

---

## 2. Descripción del Proceso de Inspección y sus Roles

### 2.1 Diagrama del Proceso (IEEE 1028 - Cláusula 6.5)

El proceso se divide en **7 etapas secuenciales estrictas**:

```
 ┌────────────────────────────────┐
 │ 1. Preparación de la Admin.    │ (Autorización de recursos y tiempo)
 └───────────────┬────────────────┘
                 ▼
 ┌────────────────────────────────┐
 │ 2. Planificación               │ (Asignación de roles, fechas y paquete de inspección)
 └───────────────┬────────────────┘
                 ▼
 ┌────────────────────────────────┐
 │ 3. Visión General (Overview)   │ (Opcional: Presentación del producto por el autor)
 └───────────────┬────────────────┘
                 ▼
 ┌────────────────────────────────┐
 │ 4. Preparación Individual      │ (Revisión autónoma usando listas de chequeo)
 └───────────────┬────────────────┘
                 ▼
 ┌────────────────────────────────┐
 │ 5. Reunión de Inspección       │ (Detección formal, lectura y registro de anomalías)
 └───────────────┬────────────────┘
                 │
                 ├─── Exit Decision (Aceptar / Retrabajo / Re-inspeccionar)
                 ▼
 ┌────────────────────────────────┐
 │ 6. Retrabajo (Rework)          │ (El Autor corrige las anomalías halladas)
 └───────────────┬────────────────┘
                 ▼
 ┌────────────────────────────────┐
 │ 7. Seguimiento y Cierre        │ (El Líder verifica la corrección de fallos)
 └───────────────┬────────────────┘
                 ▼
 ┌────────────────────────────────┐
 │ 8. Recolección de Datos        │ (Archivo de métricas para la mejora del proceso)
 └────────────────────────────────┘
```

---

### 2.2 Roles en el Equipo de Inspección (IEEE 1028 - Cláusula 6.2)

| Rol | Función Principal | ¿Puede ser el Autor? |
| :--- | :--- | :---: |
| **Inspection Leader (Líder)** | Modera la reunión, planifica la logística, vela por el cumplimiento de las reglas del estándar y verifica el retrabajo final. | **NO** |
| **Author (Autor)** | Proporciona el artefacto a inspeccionar, aclara dudas específicas en la sesión y corrige las anomalías encontradas durante el retrabajo. | **SÍ** |
| **Reader (Lector)** | Guía la lectura del producto fragmento a fragmento (parafraseando líneas de código o requisitos) para orientar al equipo durante la reunión. | **NO** |
| **Recorder (Registrador)** | Anota detalladamente cada anomalía detectada en la Lista Oficial de Hallazgos (ubicación, tipo, severidad y descripción). | **NO** |
| **Inspectors (Inspectores)** | Revisan el producto minuciosamente desde diferentes perspectivas (seguridad, rendimiento, requisitos, usabilidad, etc.). | **NO** |

---

### 2.3 Decisiones de Salida (*Exit Decision*)
Al finalizar la reunión de inspección, el equipo debe votar el estado del producto:

1. **Aceptar (Accept):** El producto se aprueba sin cambios o con correcciones muy menores que no requieren revisión.
2. **Aceptar previa verificación de retrabajo (Rework Verification):** El producto se aprueba con la condición de que el Líder de Inspección u otro integrante verifique que el Autor corrigió las anomalías registradas.
3. **Re-inspeccionar (Reinspect):** El producto contiene demasiadas anomalías o fallos críticos. Se exige corregir los errores y convocar a una **nueva reunión de inspección completa**.

---

## 3. Instructivo Paso a Paso para Aplicar el Método de Inspección

### Paso 1: Comprobar Criterios de Entrada (*Entry Criteria*)
Antes de iniciar, el Líder de Inspección debe verificar:
- [ ] El artefacto está terminado (no en borrador) y ha pasado controles sintácticos básicos (compilación, linters, correctores).
- [ ] Se dispone de los documentos fuente de referencia (especificación de requisitos, estándar de código, etc.).
- [ ] La gerencia ha asignado las horas necesarias al equipo para participar.

---

### Paso 2: Planificación y Conformación del Equipo
1. El Líder selecciona entre 3 y 6 participantes y les asigna roles (Líder, Autor, Lector, Registrador e Inspectores).
2. Se definen las **tasas de inspección recomendadas** por IEEE 1028:
   * **Documentos de Requisitos / Arquitectura:** 2 a 3 páginas por hora.
   * **Código Fuente:** 100 a 200 líneas de código por hora (LPH).
3. Se distribuye el **Paquete de Inspección** a todos los miembros (mínimo 48 horas antes):
   * Artefacto a inspeccionar.
   * Documentos de soporte / requisitos de entrada.
   * Lista de Chequeo (*Checklist*).
   * Plantilla para anotación individual de anomalías.

---

### Paso 3: Preparación Individual (Trabajo Autónomo)
* Cada participante analiza el artefacto individualmente sin interactuar con los demás.
* Utiliza la **Lista de Chequeo (*Checklist*)** para encontrar anomalías.
* Registra en su plantilla individual:
  * Las anomalías encontradas (ubicación exacta y descripción).
  * El tiempo invertido en la preparación (en minutos u horas).
* **Filtro de Calidad:** Si los inspectores no se prepararon, el Líder debe suspender la sesión.

#### Ejemplo de Lista de Chequeo Genérica para Código Fuente:
```markdown
1. [ ] ¿El código cumple con la especificación del requisito sin omitir casos de borde?
2. [ ] ¿Todas las variables y funciones tienen nombres claros y descriptivos?
3. [ ] ¿Se validan todas las entradas para evitar errores de nulos (NullPointerException)?
4. [ ] ¿Existen vulnerabilidades de seguridad (consultas SQL no parametrizadas, datos sensibles en texto plano)?
5. [ ] ¿Se gestionan de forma adecuada las excepciones y errores en los bloques try/catch?
```

---

### Paso 4: Ejecución de la Reunión de Inspección (Máx. 2 Horas)

1. **Apertura (5 min):** El Líder recuerda las reglas:
   * *"El objetivo es encontrar anomalías en el producto, no criticar a las personas"*.
   * *"No se discuten ni diseñan soluciones durante esta reunión"*.
2. **Examen Detallado (60 - 80 min):**
   * El **Lector** lee o parafrasea el producto en fragmentos pequeños (2 a 5 líneas de código o párrafos).
   * Los **Inspectores** indican las anomalías que detectaron en la preparación o durante la lectura.
   * El **Registrador** documenta formalmente cada hallazgo en la Lista Oficial de Anomalías.
3. **Consolidación de la Lista (10 min):** Se revisan los hallazgos para asegurar una redacción precisa y clara.
4. **Votación de la Decisión de Salida (5 min):** El equipo acuerda si el producto es *Aceptado*, *Aceptado con Retrabajo* o *Re-inspeccionado*.

#### Formato Oficial de Registro de Anomalías (IEEE Std 1044):

| ID Anomalía | Ubicación Exacta | Descripción del Problema | Categoría (IEEE 1044) | Severidad | Responsable de Corrección |
| :---: | :--- | :--- | :--- | :---: | :--- |
| **ANO-01** | Archivo `AuthService.js`, Línea 42 | La contraseña se almacena en texto plano en la base de datos. | Seguridad / Incumplimiento | **Crítica** | Autor |
| **ANO-02** | Documento Requisitos, Sección 3.1 | No se define qué ocurre cuando el usuario olvida su clave. | Omisión / Ambigüedad | **Marginal** | Autor |

---

### Paso 5: Retrabajo (*Rework*)
* El **Autor** recibe la Lista Oficial de Anomalías.
* Modifica y corrige el artefacto resolviendo cada punto registrado.

---

### Paso 6: Seguimiento y Cierre (*Follow-up*)
* El **Líder de Inspección** revisa la versión corregida del artefacto.
* Verifica que:
  * Todas las anomalías listadas hayan sido solucionadas.
  * No se hayan introducido nuevos errores durante la corrección.
* Una vez verificado, el Líder firma y declara el **Cierre de la Inspección**.

---

### Paso 7: Recolección de Datos y Mejora del Proceso
* Se registran las métricas finales de la inspección:
  * **Tiempo total invertido** (preparación + reunión).
  * **Líneas/páginas inspeccionadas**.
  * **Número y severidad de anomalías encontradas**.
* Estos datos se archivan para perfeccionar las listas de chequeo futuras y mejorar la productividad del equipo de desarrollo.

---

## 4. Cuadro Resumen de la Inspección de Software

| Aspecto | Descripción |
| :--- | :--- |
| **Estándar** | IEEE Std 1028-2008 (Cláusula 6) |
| **Grado de Formalidad** | Muy Alto |
| **Participantes** | 3 a 6 integrantes (Líder, Autor, Lector, Registrador, Inspectores) |
| **Participación de Gerencia** | **Estrictamente Prohibida** |
| **Métricas y Mejora** | **Mandatorio** recolectar datos de esfuerzo y anomalías |
| **Uso de Checklists** | **Obligatorio** |
| **Resultado Final** | Lista Oficial de Anomalías + Decisión de Salida (*Accept / Rework / Reinspect*) |
