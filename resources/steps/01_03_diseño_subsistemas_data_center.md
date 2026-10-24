## 📌 Paso 3: Diseño de los Subsistemas Clave del Data Center

### 1. Introducción

> *"¡Hola a todos! Ya sabemos qué disponibilidad exige nuestro software de rastreo ($99.9\%$) y seleccionamos la norma **ANSI/TIA-942 TIER III** para LogiExpress S.A.
> Ahora pasaremos de la teoría al plano físico. Construir un Data Center es como diseñar el cuerpo humano:
> * El **Cableado Estructurado** es el sistema nervioso (los datos).
> * El **Sistema Eléctrico y UPS** es el sistema circulatorio (la energía).
> * La **Climatización (HVAC)** es la regulación de temperatura (para que no sufra un 'golpe de calor').
> * La **Seguridad y Extinción de Incendios** es el sistema inmunológico (protección contra amenazas).
> 
> 
> Hoy aprenderemos cómo diseñar e interconectar cada uno de estos subsistemas para que la aplicación no falle jamás."*

---

### 2. Conceptos Clave

#### A. Cableado Estructurado (El Sistema Nervioso)

* **Concepto:** Es el conjunto de cables, conectores y dispositivos que permiten la interconexión de red dentro del Data Center de forma organizada y bajo estándar (**TIA-568** / **TIA-942**).
* **Jerarquía de Espacios en TIA-942:**
1. **ER (Entrance Room):** Donde entra la fibra óptica del proveedor público de internet (ISP).
2. **MDA (Main Distribution Area):** El núcleo de la red. Aquí residen los routers y switches centrales (*Core Switches*).
3. **HDA (Horizontal Distribution Area):** Switches de distribución que conectan hacia las filas de gabinetes/racks.
4. **ZDA (Zone Distribution Area) / EDA (Equipment Distribution Area):** El espacio final dentro de los racks donde se conectan las tarjetas de red de los servidores.


* **Medios recomendados:**
* Cable UTP Categoría 6A / 7 (para conexiones de cobre a $10\text{ Gbps}$).
* Fibra Óptica OM4/OM5 (Multimodo) o OS2 (Monomodo) para los enlaces troncales (*Backbones*).



---

#### B. Subsistema Eléctrico y Sostenibilidad (La Energía)

* **Concepto:** Proporcionar energía limpia, ininterrumpida y redundante para mantener el hardware encendido $24/7$.
* **Componentes clave:**
* **UPS de Doble Conversión en Línea:** Aísla a los servidores de picos o caídas de voltaje. Filtra la corriente y alimenta los equipos con baterías mientras entra la planta.
* **Planta Eléctrica (Generador a Diésel):** Ofrece energía de respaldo para apagones prolongados (con autonomía de al menos 24 a 48 horas).
* **PDU (Power Distribution Unit):** Regletas inteligentes ubicadas en los racks para medir el consumo de cada servidor.


* **Métrica de Sostenibilidad (PUE - Power Usage Effectiveness):**

$$\text{PUE} = \frac{\text{Energía Total Entrante al Data Center}}{\text{Energía Consumida Exclusivamente por los Servidores (TI)}}$$


* *Un PUE perfecto es $1.0$. Un Data Center eficiente maneja un PUE entre $1.2$ y $1.5$. Si el PUE es $2.0$, significa que por cada Watt que consumen los servidores, se gasta otro Watt en aire acondicionado e iluminación.*



---

#### C. Climatización y Control Ambiental (HVAC)

* **Concepto:** Evitar fallas por sobrecalentamiento (*Thermal Throttling*) o condensación/estática.
* **Estándar ASHRAE:** Mantiene la temperatura recomendada entre **$18^\circ\text{C}$ y $27^\circ\text{C}$** y la humedad relativa entre el **$40\%$ y $60\%$**.
* **Estrategia de Pasillos Fríos y Pasillos Calientes (*Hot/Cold Aisle*):**
* Los servidores aspiran aire fresco por el frente y expulsan aire caliente por la parte trasera.
* Se organizan las filas frente a frente (Pasillo Frío) y espalda con espalda (Pasillo Caliente). El pasillo frío suele cerrarse (*Cold Aisle Containment*) para maximizar la eficiencia térmica.



```
       Pasillo Frío (Aire a 18°C-22°C)
      ┌──────────────────────────────┐
      │  [FRENTE]       [FRENTE]     │
 ┌────┴────────┐       ┌─────────────┴────┐
 │ Rack Fila A │       │   Rack Fila B    │
 └────┬────────┘       └─────────────┬────┘
      │  [ATRAS]         [ATRAS]     │
      └──────────────────────────────┘
      Pasillo Caliente (Aire a 30°C-35°C)

```

---

#### D. Seguridad Física y Detección/Extinción de Incendios

* **Control de Acceso:** Biometría, tarjetas RFID, monitoreo con cámaras CCTV y puertas de seguridad (*Mantraps*).
* **Extinción de Incendios (Agentes Limpios):** **NUNCA se usa agua ni polvo químico** en un Data Center, ya que destruyen los circuitos electrónicos.
* Se utilizan gases limpios (como **FM-200**, **Novec 1230** o **Inergen**) que extinguen el fuego absorbiendo el calor o desplazando el oxígeno sin dejar residuos ni dañar los servidores.



---

### 3. Ejemplo Aplicado a *LogiExpress S.A.*

Presenta el siguiente diseño integrado a tus estudiantes:

> **El blueprint físico para LogiExpress S.A.:**
> 1. **Red:** Se instalan 2 acometidas de fibra desde la calle hasta la sala **ER**. Se conectan a un switch Core en el **MDA** y de ahí se distribuyen mediante fibra OM4 a 2 racks en el **EDA**.
> 2. **Energía:** Red eléctrica dual (**Red A** y **Red B**). Los servidores tienen doble fuente: una fuente va a la UPS A y la otra a la UPS B. Si la UPS A falla o recibe mantenimiento, la fuente B mantiene vivo el servidor.
> 3. **Clima:** 2 Unidades de Aire Acondicionado de Precisión (CRAC) en configuración $N+1$ (si se requieren 10 kW de enfriamiento, se instalan dos unidades de 10 kW por seguridad).
> 4. **Incendio:** Sistema de detección temprana de humo por aspiración (**VESDA**) y cilindros de gas **Novec 1230**.
> 
> 

---

### 4. Recursos Sugeridos para Hacer el Paso 3 Práctico en Clase (120 Minutos)

#### ⏱️ Estructura de la Sesión Práctica

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ACTIVIDAD PRÁCTICA - CORTE 1 (PASO 3)                │
│             Diseño Físico y Subsistemas del Data Center                 │
└─────────────────────────────────────────────────────────────────────────┘
  [00-20 min] ──> Exposición de los 4 Subsistemas y Estándares
  [20-50 min] ──> Ejercicio 1: Cálculo de PUE y Carga Térmica/Eléctrica
  [50-95 min] ──> Ejercicio 2: Taller de Layout en Sweet Home 3D o Draw.io
  [95-115 min]──> Ejercicio 3: Simulación de Incendio y Falla Eléctrica
  [115-120 min]─> Cierre del Corte 1 y Consolidación del Entregable

```

---

#### 🛠️ Especificación de los Ejercicios Prácticos

##### Ejercicio 1: Calculadora de PUE y Capacidad Térmica (30 Minutos)

* **Objetivo:** Aplicar conceptos matemáticos reales de consumo eléctrico y enfriamiento.
* **Dinámica:** Pide a los estudiantes resolver el siguiente caso en grupos:
1. **Datos de los servidores de LogiExpress:**
* 10 Servidores en Rack, cada uno consume $500\text{ Watts}$. Consumo total de TI = $5,000\text{ W}$ ($5\text{ kW}$).
* El sistema de aire acondicionado y luces consume $3,500\text{ W}$ ($3.5\text{ kW}$).


2. **Cálculos requeridos:**
* **Consumo Total:** $5\text{ kW} + 3.5\text{ kW} = 8.5\text{ kW}$.
* **PUE:** $\text{PUE} = \frac{8.5\text{ kW}}{5.0\text{ kW}} = \mathbf{1.7}$.
* **Pregunta de reflexión:** *"Si logramos aislar el pasillo frío y reducir el consumo del aire a $1.5\text{ kW}$, ¿cuál sería el nuevo PUE?"*
* $\text{Nuevo PUE} = \frac{6.5}{5.0} = \mathbf{1.3}$ (Ahorro energético sustancial).







---

##### Ejercicio 2: Taller de Layout Físico del Data Center (45 Minutos)

* **Objetivo:** Crear el mapa o plano a escala con la distribución física de la sala del Data Center.
* **Herramienta:** **Draw.io** (módulo de planos de planta / *Floor Plan*) o software libre de arquitectura como **Sweet Home 3D**.
* **Instrucciones para los estudiantes:** Debe diseñar un cuarto de $6 \times 4\text{ metros}$ e incluir de forma visual y ordenada:
* Puerta de acceso biométrico con esclusa de seguridad.
* 2 Filas de Racks organizadas en Pasillo Frío (con baldosas perforadas en el piso falso) y Pasillo Caliente.
* Gabinete para la UPS y el tablero de distribución eléctrica (PDU).
* 2 Unidades de Aire Acondicionado de Precisión (CRAC) en los extremos.
* Boquillas del sistema de gas de extinción de incendios en el techo.



---

##### Ejercicio 3: "Simulación de Crisis en el Data Center" (20 Minutos)

* **Objetivo:** Evaluar la resiliencia del diseño creado por cada grupo.
* **Dinámica:** El docente lanza dos imprevistos a cada grupo y los estudiantes deben explicar cómo su diseño evita que el software de LogiExpress se detenga:
* **Crisis A:** *"Un cortocircuito destruye la UPS principal a las 2:00 AM."*
* *Respuesta esperada:* Como el sistema es TIER III con doble circuito (Red A / Red B), la UPS B asume la carga y las baterías alimentan el sistema mientras entra la planta a diésel.


* **Crisis B:** *"Se produce un connato de incendio en el Rack 2 por una fuente defectuosa."*
* *Respuesta esperada:* El sensor VESDA detecta el humo, activa la alarma, cierra los dampers de aire acondicionado e inyecta gas Novec 1230 para ahogar el fuego sin dañar los servidores ni mojar el suelo.