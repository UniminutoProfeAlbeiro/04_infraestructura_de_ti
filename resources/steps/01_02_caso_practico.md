Aquí tienes la especificación **paso a paso y minuto a minuto** para llevar a cabo la sesión práctica del **Paso 1** en el aula de clase. Está diseñada para un bloque estándar de **2 horas (120 minutos)** o para adaptarse a tus tiempos directos de acompañamiento.

---

## ⏱️ Estructura y Guiña de Clase Práctica (120 Minutos)

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