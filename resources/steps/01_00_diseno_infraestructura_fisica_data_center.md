## 🏗️ Corte 1: Diseño de Infraestructura Física y Data Center

### 1. El Caso de Estudio: *"LogiExpress S.A."*

> **Contexto:** *LogiExpress S.A.* es una empresa colombiana de logística y distribución nacional. Debido a la expansión de sus operaciones, su sistema de rastreo de flotas en tiempo real (software crítico) y su base de datos de envíos sufren caídas constantes por fallas eléctricas y falta de capacidad en su cuarto de servidores actual. La gerencia ha decidido diseñar desde cero un **Data Center moderno** ubicado en su sede principal.

---

### 2. Paso a Paso

**RAC_01**: *Explica los distintos componentes, funcionalidad y dispositivos utilizados en un despliegue de TI, teniendo en cuenta las normas internacionales*:

#### **Paso 1: Análisis de Requerimientos y Carga (El Negocio y el Software)**

* **Qué hacer:** Identificar qué servicios de software correrán allí (ej. bases de datos relacionales, APIs de rastreo, sistema ERP).
* **Explicación:** La infraestructura existe *para garantizar que el software no falle*. Si el software requiere alta disponibilidad (24/7), la infraestructura física debe respaldarlo.

#### **Paso 2: Selección de la Norma Internacional (Estándar ANSI/TIA-942)**

* **Qué hacer:** Los estudiantes deben investigar la norma **ANSI/TIA-942** (*Telecommunications Infrastructure Standard for Data Centers*).
* **Ejercicio práctico:** Deben decidir qué **Nivel TIER** (Tier I, II, III o IV) necesita *LogiExpress S.A.*
* **Explicación:** Como es una empresa de distribución nacional que no puede parar, un **Tier III** (mantenimiento concurrente, redundancia N+1) es el punto óptimo de discusión.



#### **Paso 3: Diseño de los Subsistemas del Data Center**

Desglosar el diseño físico estructurado en componentes clave:

1. **Cableado Estructurado:** Distribución de fibra óptica y cable UTP categoría 6A/7 entre el cuarto de telecomunicaciones (TR) y el área principal (MDA/HDA).
2. **Sistema Eléctrico y Sostenibilidad:** UPS (sistemas de alimentación ininterrumpida), plantas eléctricas de emergencia y eficiencia energética (PUE - *Power Usage Effectiveness*).
3. **Climatización (HVAC):** Control preciso de temperatura y humedad (pasillos fríos / pasillos calientes) para evitar daños en los servidores.
4. **Seguridad Física y Monitoreo:** Control de acceso biométrico, cámaras CCTV y sistemas de detección/extinción de incendios (ej. agentes limpios).

#### **Paso 4: El Entregable del Estudiante**

* **Blueprint / Diagrama Topológico:** Un plano esquemático (pueden usar herramientas gratuitas como *Lucidchart*, *Draw.io* o incluso un plano bien estructurado) que muestre la distribución física del Data Center de LogiExpress.
* **Documento Técnico Breve:** Justificando por qué eligieron ese nivel TIER y cómo cada subsistema cumple con la norma ANSI/TIA-942.