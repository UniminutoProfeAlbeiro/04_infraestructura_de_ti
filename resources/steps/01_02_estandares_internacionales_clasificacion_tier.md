Aquí tienes la guía explicativa y práctica detallada para el **Paso 2: Selección de la Norma Internacional y Niveles TIER (ANSI/TIA-942)**, estructurada exactamente con el lenguaje, conceptos y dinámica paso a paso para tus estudiantes.

---

## 📌 Paso 2: Estándares Internacionales y Clasificación TIER (ANSI/TIA-942)

### 1. Mensaje introductorio para tus estudiantes (Guion de Clase)

> *"¡Hola a todos! En el paso anterior definimos los requerimientos de software de LogiExpress S.A. y entendimos que nuestra aplicación necesita una alta disponibilidad ($99.9\%$). Ahora surge la pregunta del millón: **¿Cómo construimos o elegimos un Data Center sin adivinar ni 'inventar la rueda'?**
> Para eso existen los estándares internacionales. Hoy aprenderemos a utilizar la norma **ANSI/TIA-942**, que es la guía definitiva en ingeniería para diseñar la arquitectura física, eléctrica y de telecomunicaciones de un Data Center. Veremos los **Niveles TIER**, que nos indican qué tan 'a prueba de fallas' es una infraestructura."*

---

### 2. Conceptos Clave que debes enseñarles

#### A. ¿Qué es la norma ANSI/TIA-942?

* **Concepto:** Es el estándar dictado por la *Telecommunications Industry Association* (TIA) que establece los requisitos mínimos para la infraestructura de telecomunicaciones de los Data Centers y salas de ordenadores.
* **Aspectos que evalúa:**
1. **Telecomunicaciones:** Cableado estructurado, redundancia de canalizaciones y proveedores de internet.
2. **Arquitectura/Estructura:** Ubicación geográfica, protección contra inundaciones/terremotos, resistencia de pisos y seguridad de accesos.
3. **Sistema Eléctrico:** Fuentes de alimentación, plantas eléctricas, UPS y distribución de energía.
4. **Sistemas Mecánicos:** Climatización (aire acondicionado de precisión), control de humedad y extinción de incendios.



#### B. Clasificación de Niveles TIER (Uptime Institute / TIA-942)

Explícales que los **TIER (I al IV)** miden la **disponibilidad** y la **tolerancia a fallos** de la infraestructura:

```
+──────────────────────────────────────────────────────────────────────────+
|  TIER I   │ Capacidad Básica         │ Sin redundancia         │ 99.671% |
|  TIER II  │ Componentes Redundantes  │ Redundancia N+1 (Parcial)│ 99.741% |
|  TIER III │ Mantenimiento Concurrente│ Redundancia N+1 Activa  │ 99.982% |
|  TIER IV  │ Tolerante a Fallos       │ Redundancia 2N o 2(N+1) │ 99.995% |
+──────────────────────────────────────────────────────────────────────────+

```

1. **TIER I (Básico):**
* **Definición:** Una sola vía de distribución eléctrica y de refrigeración, sin componentes redundantes ($N$).
* **Efecto:** Si se le hace mantenimiento o falla una pieza, el Data Center **se apaga**.
* **Tiempo de caída:** Hasta **28.8 horas al año**.


2. **TIER II (Componentes Redundantes):**
* **Definición:** Incluye componentes redundantes ($N+1$), pero mantiene una sola vía de distribución de energía y clima.
* **Efecto:** Puede soportar la falla de un motor o una UPS, pero un corte en las tuberías o cables detiene el sistema.
* **Tiempo de caída:** Hasta **22 horas al año**.


3. **TIER III (Mantenimiento Concurrente - El Estándar Recomendado):**
* **Definición:** Múltiples vías de distribución eléctrica y de enfriamiento, pero solo **una activa y otra en reserva (pasiva)**. Componentes redundantes ($N+1$).
* **Efecto:** Permite reparar o reemplazar cualquier componente (un transformador, un aire, una UPS) **sin apagar los servidores**.
* **Tiempo de caída:** Máximo **1.6 horas (95 minutos) al año**.


4. **TIER IV (Tolerante a Fallos / Fault Tolerant):**
* **Definición:** Múltiples vías activas y simultáneas ($2N$ o $2(N+1)$).
* **Efecto:** Si ocurre una falla grave imprevista en un lado, la carga pasa al otro lado al instante sin interrupción.
* **Tiempo de caída:** Máximo **26 minutos al año**. (Es sumamente costoso, usado por bancos, entidades militares o gigantes cloud).



---

### 3. Ejemplo Aplicado al Caso *LogiExpress S.A.*

Presentales el siguiente dilema de toma de decisiones de ingeniería:

> **El dilema de LogiExpress:**
> * **Opción TIER II:** Es económica, pero cuando toque hacerle mantenimiento a la planta eléctrica o a la UPS, habrá que apagar el servidor de rastreo por 4 horas. *Impacto:* Camiones perdidos en carretera y multas de clientes.
> * **Opción TIER IV:** Es $100\%$ invulnerable, pero el costo de construcción supera el presupuesto de la empresa por $300\%$.
> * **Solución Óptima (TIER III):** Permite hacer mantenimiento a la infraestructura en caliente (mientras la app sigue corriendo) y ofrece la disponibilidad del $99.9\%$ que requiere el software de LogiExpress, optimizando los costos.
> 
> 

---

### 4. Recursos Sugeridos para Hacer el Paso 2 Práctico en Clase (120 Minutos)

#### ⏱️ Estructura de la Sesión Práctica

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ACTIVIDAD PRÁCTICA - CORTE 1 (PASO 2)                │
│    Selección de la Norma ANSI/TIA-942 y Justificación de Nivel TIER     │
└─────────────────────────────────────────────────────────────────────────┘
  [00-20 min] ──> Exposición Interactiva de la Norma ANSI/TIA-942
  [20-50 min] ──> Ejercicio 1: Comparador de Costos vs. Disponibilidad
  [50-90 min] ──> Ejercicio 2: Matriz de Decisiones TIER para LogiExpress
  [90-115 min]──> Ejercicio 3: Check-list Normativo de Subestaciones
  [115-120 min]─> Cierre e Integración con el Informe del Corte 1

```

---

#### 🛠️ Especificación de los Ejercicios Prácticos

##### Ejercicio 1: Calculadora de Costos de Inactividad (*Cost of Downtime*) (30 Minutos)

* **Objetivo:** Que los estudiantes argumenten el costo-beneficio de elegir un Nivel TIER utilizando dólares o pesos.
* **Herramienta:** Hoja de cálculo (Excel / Google Sheets) o calculadora.
* **Dinámica:**
1. Entrégales los siguientes datos de *LogiExpress S.A.*:
* **Pérdida por hora de inactividad:** USD $5,000 (ventas no registradas, penalizaciones de contratos y horas extra de conductores).


2. Pídeles calcular las pérdidas anuales por nivel TIER basándose en el tiempo máximo de caída:
* **TIER I (28.8 hrs/año de caída):** $28.8 \times \$5,000 = \mathbf{\$144,000\text{ USD/año en pérdidas}}$.
* **TIER II (22 hrs/año de caída):** $22 \times \$5,000 = \mathbf{\$110,000\text{ USD/año en pérdidas}}$.
* **TIER III (1.6 hrs/año de caída):** $1.6 \times \$5,000 = \mathbf{\$8,000\text{ USD/año en pérdidas}}$.
* **TIER IV (0.4 hrs/año de caída):** $0.4 \times \$5,000 = \mathbf{\$2,000\text{ USD/año en pérdidas}}$.


3. **Conclusión en clase:** Reducir la caída de un TIER I/II a un TIER III le ahorra a la empresa más de $100,000 USD al año, justificando la inversión en un Data Center TIER III.



---

##### Ejercicio 2: Taller de Matriz de Selección TIER (40 Minutos)

* **Objetivo:** Justificar la elección del nivel TIER teniendo en cuenta los criterios de evaluación del Acuerdo Pedagógico (*Excepcional: Demuestra el funcionamiento integral de un Data Center a partir de un caso propuesto*).
* **Metodología:** En los mismos grupos de trabajo (máximo 3 estudiantes).
* **Instrucción para los estudiantes:** Deben diligenciar una tabla justificativa en sus cuadernos o computadores respondiendo a estas tres preguntas clave:

| Pregunta de Diseño | Respuesta Técnica basada en TIA-942 | Justificación para LogiExpress |
| --- | --- | --- |
| **¿Qué nivel TIER se elige y por qué?** | TIER III. | Ofrece mantenimiento concurrente sin detener los servicios del software de rastreo. |
| **¿Cómo debe ser la distribución eléctrica?** | Caminos duales (Red A + Red B), una activa y una en espera. | Si se quema un tablero de control, el tablero secundario toma el control de inmediato. |
| **¿Qué capacidad de reserva en energía y refrigeración requiere?** | Redundancia $N+1$. | Si el Data Center requiere 2 aires acondicionados, se deben instalar 3 ($2+1$). |

---

##### Ejercicio 3: Tour Virtual / Análisis de Caso Real (25 Minutos)

* **Objetivo:** Ver en la vida real cómo se distribuye un Data Center bajo la norma TIA-942.
* **Recurso:** Usar un vídeo corto de recorrido por un Data Center Certificado TIER III / TIER IV (por ejemplo, recorridos públicos de Data Centers de *Equinix*, *Google* o *AWS* disponibles en YouTube).
* **Dinámica:** Mientras ven el vídeo de 5-8 minutos, los estudiantes deben tomar nota e identificar:
1. ¿Dónde están ubicadas las plantas eléctricas y tanques de diésel?
2. ¿Cómo están divididos los pasillos fríos y calientes?
3. ¿Cómo es el control de acceso físico en la entrada?