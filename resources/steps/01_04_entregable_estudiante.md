## 📌 Paso 4: Consolidación y Presentación del Blueprint Técnico del Data Center

### 1. Introducción

> *"¡Felicitaciones a todos! Hemos recorrido un camino completo: analizamos los requerimientos de la aplicación de LogiExpress S.A., seleccionamos la norma **ANSI/TIA-942 TIER III** y diseñamos minuciosamente los cuatro subsistemas del Data Center.*
> *Ahora llega el momento más importante en la vida profesional de un ingeniero de sistemas: **saber comunicar y vender una solución técnica**. Un diseño brillante no sirve de nada si no sabemos plasmarlo en una propuesta ejecutiva clara, estructurada y respaldada por normas internacionales.*
> *En este Paso 4 aprenderemos a consolidar la documentación técnica y a sintetizar nuestra arquitectura en un vídeo ejecutivo de 3 minutos."*

---

### 2. Conceptos Clave

#### A. Estructura de una Propuesta Técnica de Infraestructura

Explícales que una propuesta técnica para la gerencia o un cliente no es un ensayo largo sin forma, sino un documento modular con secciones estándar de la industria:

1. **Resumen Ejecutivo:** Un párrafo que sintetiza el problema de negocio de LogiExpress S.A. y el beneficio principal de la solución propuesta.
2. **Matriz de Requerimientos vs. SLA:** Explicación de los "Nueves de Disponibilidad" y por qué se requiere una infraestructura $99.9\%$ disponible.
3. **Justificación Normativa (TIA-942 / TIER III):** Argumentación técnica y económica de por qué TIER III es la elección óptima (mantenimiento concurrente sin apagar servicios).
4. **Planos y Diagramas de Subsistemas:**
* Diagrama lógico de red en **Draw.io** (routers, switches, firewalls).
* Plano físico/Layout de la sala de cómputo (pasillos fríos/calientes, Racks, UPS, aire acondicionado, extintores).


5. **Matriz de Análisis de Riesgos y Mitigación:** Identificación de puntos únicos de falla (SPOF) y cómo la infraestructura los resuelve.

---

#### B. La Técnica de Pitch Ejecutivo (Vídeo de 3 Minutos)

Enseña a tus estudiantes que el vídeo de sustentación (*UN_01_EX*) requiere capacidad de síntesis, precisión técnica y dinamismo:

* **Estructura del vídeo (Regla de los 3 Bloques / 60 segundos por bloque):**
* **Minuto 1 (El Problema y la Solución Normativa):** Presentación del caso de LogiExpress S.A. y justificación de la norma TIA-942 TIER III.
* **Minuto 2 (El Blueprint Físico y Lógico):** Recorrido visual por el plano del Data Center y los subsistemas de energía, red y clima.
* **Minuto 3 (Demostración de Resiliencia / Caso de Prueba):** Simulación de una falla (ej. caída de energía o falla de un aire) y explicación de cómo la infraestructura la absorbe sin afectar el software de rastreo.



---

### 3. Matriz de Autoevaluación para los Estudiantes

Muestra esta lista de chequeo a tus estudiantes para que verifiquen si su trabajo cumple con los niveles del criterio de evaluación antes de enviarlo:

| Elemento del Entregable | Nivel Esperado | Nivel Excepcional |
| --- | --- | --- |
| **Paso 1: Análisis** | Explica la funcionalidad de los componentes de red según normas. | Mapea la carga de la API con los tiempos de respuesta e impacto en el negocio. |
| **Paso 2: Norma TIER** | Selecciona la norma ANSI/TIA-942 y describe el TIER III. | Compara el costo del *downtime* vs. la inversión en TIER III con métricas numéricas. |
| **Paso 3: Subsistemas** | Muestra diagramas de red y consumo eléctrico básico. | Presenta layout en pasillo frío/caliente, PUE de la sala y simulación de contingencia. |
| **Paso 4: Presentación** | Entrega documento en PDF y vídeo descriptivo de 3 minutos. | **Demuestra el funcionamiento integral del Data Center mediante la resolución de un caso simulado de falla.** |

---

### 4. Recursos Sugeridos para Hacer el Paso 4 Práctico en Clase (120 Minutos)

#### ⏱️ Estructura de la Sesión Práctica

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ACTIVIDAD PRÁCTICA - CORTE 1 (PASO 4)                │
│            Consolidación del Entregable y Simulación de Pitch           │
└─────────────────────────────────────────────────────────────────────────┘
  [00-20 min] ──> Explicación de la Estructura del Informe y Rúbrica
  [20-50 min] ──> Ejercicio 1: Taller de Redacción de Resumen Ejecutivo y Riesgos
  [50-95 min] ──> Ejercicio 2: Ensayos de Pitch de 3 Minutos (Simulación en Aula)
  [95-115 min]──> Ejercicio 3: Revisiones Cruzadas (Peer Review entre Equipos)
  [115-120 min]─> Indicaciones Finales de Carga en Aula Virtual y Cierre

```

---

#### 🛠️ Especificación de los Ejercicios Prácticos

##### Ejercicio 1: Taller de Redacción de Riesgos y Resumen Ejecutivo (30 Minutos)

* **Objetivo:** Sintetizar la propuesta técnica en una sección ejecutiva clara.
* **Metodología:** En los grupos de trabajo (máx. 3 personas).
* **Actividad:** Pide a los equipos redactar un párrafo de 150 palabras que venda el proyecto a la junta directiva de LogiExpress S.A.
* **Plantilla de ayuda para el estudiante:**
> *"Para respaldar la operación del sistema de rastreo de LogiExpress S.A. y garantizar una disponibilidad del $99.9\%$, proponemos la construcción de un Data Center diseñado bajo la norma **ANSI/TIA-942 Nivel TIER III**. Esta arquitectura incorpora redundancia $N+1$ en energía y climatización, eliminando puntos únicos de falla (SPOF) y permitiendo mantenimientos preventivos sin interrumpir la operación del software. La solución reduce las pérdidas anuales por inactividad a menos de 1.6 horas al año, optimizando los costos mediante un PUE estimado de 1.3." *



---

##### Ejercicio 2: Ensayos del Pitch en Vivo de 3 Minutos (45 Minutos)

* **Objetivo:** Entrenar la comunicación oral y la síntesis para el vídeo *UN_01_EX*.
* **Dinámica:**
1. Cada grupo selecciona a un integrante o se dividen el guion en 3 partes de 1 minuto.
2. Pide a 2 o 3 grupos que pasen al frente del salón (o abran micrófono) y proyecten sus planos de Draw.io mientras realizan un ensayo de 3 minutos cronometrados.
3. **Retroalimentación inmediata del profesor:** Evalúa si explicaron el estándar TIA-942, si el plano es legible y si demostraron cómo reacciona el Data Center ante una falla.



---

##### Ejercicio 3: Evaluación por Pares (*Peer Review*) (20 Minutos)

* **Objetivo:** Aplicar retroalimentación antes de la entrega definitiva en la plataforma.
* **Dinámica:**
1. El Grupo A intercambia su borrador de documento/diagrama con el Grupo B.
2. Cada grupo debe revisar el trabajo del otro usando la lista de chequeo (Pasos 1 a 3) e identificar al menos:
* Un punto único de falla (SPOF) no resuelto en el diagrama.
* Una mejora en el diseño del pasillo frío/caliente o en el tipo de cableado.


3. Devuelven las observaciones para que cada equipo ajuste su entrega final.



---

### 📦 Check-list de Entrega Final

Recordatorio de los parámetros formales para cargar en el Aula Virtual según el acuerdo pedagógico:

* **Formato de Trabajo:** Colaborativo (máximo 3 integrantes).
* **Entregable 1 (UN_01_EN):** Documento consolidado en PDF con la justificación normativa, matriz de disponibilidad, diagramas de Draw.io y layout del Data Center.
* **Entregable 2 (UN_01_EX):** Enlace al vídeo de sustentación de 3 minutos publicado en Teams, Stream o YouTube (modo oculto).
* **Canal de Entrega:** Exclusivamente la plataforma Aula Virtual.