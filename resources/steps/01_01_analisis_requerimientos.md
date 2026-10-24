## 📌 Paso 1: Análisis de Requerimientos de Software e Impacto en la Infraestructura TI

### 1. Introducción

> *"Bienvenidos. Muchos de ustedes probablemente piensen que la infraestructura física (servidores, cables, aires acondicionados y plantas eléctricas) es un tema aislado del desarrollo de software. La realidad es totalmente opuesta: **el software determina la infraestructura y la infraestructura condiciona al software**.*
> *Si desarrollamos una aplicación web o una API crítica y la infraestructura donde corre se cae por un corte de energía o un sobrecalentamiento, nuestro código simplemente no sirve de nada. En este primer paso del caso LogiExpress S.A., nuestro objetivo no es instalar cables ni comprar servidores aún; es **entender las necesidades del software y del negocio para traducirlas en requerimientos de infraestructura**."*

---

### 2. Conceptos Clave:

#### A. Disponibilidad del Sistema (Availability & SLAs)

* **Concepto:** Porcentaje de tiempo que un sistema de software debe estar operativo y accesible para los usuarios. Se mide formalmente a través del **SLA (Service Level Agreement)** o Acuerdo de Nivel de Servicio.
* **Métrica clave ("Los Nueves"):**
* **99% (Dos nueves):** Puede estar caído hasta **3.65 días al año**.
* **99.9% (Tres nueves):** Tiempo de caída máximo de **8.76 horas al año**.
* **99.99% (Cuatro nueves - Estándar para sistemas críticos):** Tiempo de caída máximo de **52.6 minutos al año**.


* **Ejemplo para el caso:** LogiExpress S.A. tiene un software de rastreo de flota por GPS. Si la API de recepción de eventos GPS se cae durante 2 horas en hora pico, se pierden miles de paquetes y rutas de camiones. Por tanto, el software exige una disponibilidad mínima de **99.9% o superior**.

#### B. Perfil de Carga y Capacidad (Compute, Memory & I/O)

* **Concepto:** Estimar los recursos físicos que demandará la carga de trabajo (*Workload*) del software.
* **Componentes del análisis:**
* **Cómputo y Memoria (CPU / RAM):** ¿Cuántas peticiones concurrentes por segundo procesará la aplicación?
* **Entrada/Salida y Almacenamiento (I/O & Storage):** ¿Qué volumen de lecturas y escrituras por segundo (IOPS) genera la base de datos de envíos?


* **Ejemplo para el caso:** LogiExpress tiene 500 camiones reportando ubicación cada 10 segundos. Esto genera $50 \text{ peticiones/segundo}$ hacia el servidor web y la base de datos de PostgreSQL. Se requiere almacenamiento de alta velocidad (SSDs NVMe) y un arreglo de discos en **RAID 10** para garantizar rendimiento y tolerancia a fallos.

#### C. Tolerancia a Fallos y Redundancia (*Single Point of Failure - SPOF*)

* **Concepto:** Identificar cualquier componente de software o hardware cuya falla cause la caída de todo el sistema.
* **Ejemplo para el caso:** Si la base de datos corre en un único servidor conectado a una sola fuente de energía, esa fuente es un **SPOF**. Si la luz falla, el software se apaga. La infraestructura debe ofrecer **doble acometida eléctrica (red A y red B)** y la base de datos debe tener replicación/failover.

#### D. Tiempo de Recuperación (RTO y RPO)

* **Concepto:**
* **RTO (Recovery Time Objective):** ¿Cuánto tiempo máximo puede estar fuera de servicio el software mientras se soluciona una falla?
* **RPO (Recovery Point Objective):** ¿Cuántos datos se pueden permitir perder (en tiempo) desde el último respaldo?



---

### 3. Matriz de Mapeo: Del Requerimiento de Software al Componente de Infraestructura

| Requerimiento del Software (LogiExpress S.A.) | Impacto / Requerimiento en Infraestructura Física |
| --- | --- |
| La API de rastreo no puede detenerse por apagones eléctricos. | **UPS de doble conversión en línea** + **Planta eléctrica a diésel** con autonomía mínima de 24h. |
| La base de datos relacional procesa transacciones constantes de paquetes. | Servidores con **fuentes de alimentación redundantes**, discos **SSD NVMe enterprise** y arreglo **RAID**. |
| El backend genera altas temperaturas por procesamiento constante de peticiones HTTP. | Sistema de **aire acondicionado de precisión (HVAC)** configurado en pasillo frío / pasillo caliente. |
| Interconexión segura entre la app móvil de los conductores y el Data Center. | **Firewall de hardware**, routers redundantes y conexiones de red de fibra óptica con dos proveedores (ISP) distintos. |

---

### 4. Caso Práctico

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ACTIVIDAD PRÁCTICA - CORTE 1                         │
│   Traduciendo Requerimientos de Software a Infraestructura de TI        │
└─────────────────────────────────────────────────────────────────────────┘
  [00-15 min] ──> Introducción y Contexto (LogiExpress S.A.)
  [15-35 min] ──> Ejercicio 1: Simulación de SLA y Tiempo de Caída
  [35-75 min] ──> Ejercicio 2: Cacería de Puntos Únicos de Falla (SPOF)
  [75-110 min]──> Ejercicio 3: Elaboración del Diagrama Lógico en Draw.io
  [110-120 min]─> Cierre y Enlace con el Entregable del Corte

```

---

### 1. Introducción y Contexto de Negocio (15 Minutos)

1. **Planteamiento del escenario:**
* Presenta a los estudiantes la ficha de la empresa *LogiExpress S.A.*:
* **Operación:** 500 camiones de reparto en Colombia enviando datos de GPS cada 10 segundos.
* **Problema:** El sistema actual se cae cuando se va la luz o cuando se calientan los servidores caseros, provocando pérdida de rastreo y multas por incumplimiento de entregas.




2. **Pregunta detonante para el grupo:**
> *"Si ustedes programaron la API REST que recibe las ubicaciones GPS, ¿cuánto tiempo al año aceptan que esa API no responda porque el servidor físico se apagó?"*



---

### 2. Ejercicio Práctico 1: Simulación de SLA y Tiempo de Caída (20 Minutos)

**Objetivo:** Que los estudiantes entiendan de forma matemática y directa qué significa la disponibilidad de un sistema (*"Los Nueves"*).

* **Herramienta:** Navegador web en el sitio libre **[uptime.is](https://uptime.is/)**.
* **Paso a Paso:**
1. Pide a los estudiantes que abran en sus computadores o teléfonos el enlace `[https://uptime.is/](https://uptime.is/)`.
2. Indícales que ingresen los siguientes porcentajes de disponibilidad y completen una tabla individual o en parejas:
* **99% (Dos nueves):** Observar el tiempo de caída al año ($\approx 3.65$ días).
* **99.9% (Tres nueves):** Observar el tiempo de caída al año ($\approx 8.76$ horas).
* **99.99% (Cuatro nueves):** Observar el tiempo de caída al año ($\approx 52.6$ minutos).


3. **Discusión en clase (5 min):**
* Pregúntales: *"Para LogiExpress S.A., ¿cuál nivel de SLA es aceptable si la empresa opera 24/7 y no puede detenerse?"*
* **Conclusión guiada:** Se elegirá un objetivo de **99.9% (Tier III)**, lo que implica que la infraestructura física debe estar diseñada para no fallar más de 8 horas al año en mantenimiento o imprevistos.





---

### 3. Ejercicio Práctico 2: "Cacería de Puntos Únicos de Falla (SPOF)" (40 Minutos)

**Objetivo:** Desarrollar el pensamiento crítico para identificar vulnerabilidades físicas antes de diseñar el Data Center.

* **Metodología:** Trabajo colaborativo en grupos de máximo 3 estudiantes (según el acuerdo pedagógico).
* **Paso a Paso:**
1. **Proyecta en el tablero el siguiente escenario frágil (SPOF inicial):**
> *La API de LogiExpress corre en 1 servidor físico. Este servidor está conectado a 1 solo tomacorriente de la pared, a 1 solo switch de red, y la empresa tiene contratado 1 solo proveedor de internet (ISP).*


2. **Entregable en clase (20 min):** Cada equipo debe listar al menos **5 Puntos Únicos de Falla (SPOF)** y escribir la solución física para cada uno.
3. **Puesta en común (15 min):** Pide a 2 o 3 grupos que compartan una falla encontrada.



#### 📄 Guía de Respuestas Esperadas (Para ti como Docente):

| Componente Frágil (SPOF) | Falla Probable | Solución de Infraestructura |
| --- | --- | --- |
| Tomacorriente único | Si falla la energía de la calle, todo colapsa. | **UPS de doble conversión** + **Planta eléctrica**. |
| Fuente del servidor | Si se quema la fuente del servidor, el servidor se apaga. | Servidor con **doble fuente de poder redundante (Red A / Red B)**. |
| Un solo switch de red | Si el switch falla, el servidor queda incomunicado. | Arreglo de **switches redundantes (Stacking)**. |
| Un solo proveedor de Internet | Si el operador de internet falla, la flota queda a ciegas. | **Doble enlace de Internet (Enlaces multicarrier / BGP)** con rutas físicas distintas. |
| Un solo disco duro | Si el disco colapsa, se pierden las rutas registradas. | Arreglo de discos en **RAID 10 (Redundancia + Rendimiento)**. |

---

### 4. Ejercicio Práctico 3: Diagramado de la Arquitectura Lógica (35 Minutos)

**Objetivo:** Mapear la solución del software dentro de un flujo de infraestructura redundante.

* **Herramienta:** **Draw.io (diagrams.net)** — Gratuita y accesible sin registro obligatorio.
* **Paso a Paso:**
1. Pide a cada grupo abrir `[https://app.diagrams.net/](https://app.diagrams.net/)`.
2. Indícales seleccionar la plantilla en blanco (*Blank Diagram*) o usar las formas del paquete de red (*Network / Cloud*).
3. **Instrucción de diseño:** Deben graficar la arquitectura lógica que conectará a la flota con el Data Center de LogiExpress S.A., incluyendo:
* **Clientes:** App Móvil / Camiones GPS.
* **Entrada:** 2 Proveedores de Internet (ISP 1 e ISP 2) + Firewall de hardware redundante.
* **Red Interna:** Switches de distribución redundantes.
* **Servidores:** 2 Servidores Web (balanceados) + 1 Servidor de Base de Datos principal con réplica.
* **Respaldo Energético:** UPS conectada a dos redes eléctricas independientes.


4. **Supervisión activa:** Camina por el salón o revisa las pantallas de los estudiantes orientándolos si conectan un componente de manera aislada o dejan algún SPOF.



---

### 5. Cierre de la Sesión y Conexión con el Entregable (10 Minutos)

1. **Resumen de la sesión:** Recalca cómo las decisiones que tomaron hoy (evitar SPOFs y garantizar el SLA) son las que van a guiar el diseño del Data Center según la norma **ANSI/TIA-942** en la siguiente fase.
2. **Instrucción para la entrega del Corte 1:**
* Indícales que el diagrama lógico trabajado hoy en **Draw.io** formará parte del anexo del informe colaborativo (*UN_01_EN: Análisis normativo y estructural de infraestructura TI*) y servirá de base para el vídeo explicativo de 3 minutos (*UN_01_EX*).