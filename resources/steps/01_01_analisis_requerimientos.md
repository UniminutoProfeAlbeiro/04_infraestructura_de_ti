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

