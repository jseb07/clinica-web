# Simulación estocástica de atención de pacientes en una clínica

Página web interactiva del proyecto del curso **Modelamiento y Simulación**
(Universidad de San Buenaventura, Medellín). Implementa una simulación de
**eventos discretos** de una cola **M/M/c** con prioridad no apropiativa y
sala de espera de capacidad finita, directamente en el navegador.

**Autores:** Juan Sebastián Brunal · Juan Sebastián Calvo · Simón Valencia

## ¿Qué hace?

- Simula la atención de **1 000 pacientes** ajustando en vivo: número de
  médicos *c*, tasa de llegadas λ, duración media de consulta, probabilidad
  de paciente urgente, capacidad de la sala *K* y semilla aleatoria.
- Calcula y muestra los indicadores clave: espera media en cola, espera por
  prioridad, tiempo en el sistema, utilización de los médicos y probabilidad
  de rechazo.
- Grafica la dinámica de la cola en el tiempo, el histograma de tiempos de
  espera y un análisis de sensibilidad del número de médicos.
- Genera un **dataset sintético de 1 000 pacientes** descargable como CSV.

## Cómo abrirlo

Solo abre el archivo `index.html` en cualquier navegador moderno (Chrome,
Firefox, Edge, Safari). No requiere instalación; los gráficos se cargan
mediante [Chart.js](https://www.chartjs.org/) desde un CDN.

## Detalles técnicos

El simulador (en JavaScript puro) implementa:

- **Cola de prioridad de eventos** con un min-heap binario.
- **PRNG sembrado** (Mulberry32) para resultados reproducibles.
- Generación de tiempos exponenciales por **transformada inversa**.
- **Integración en el tiempo** de las variables de estado para estimar
  *Lq*, *L* y la utilización.
- **Prioridad no apropiativa**: los pacientes urgentes pasan al frente de
  la cola pero no interrumpen una consulta en curso.

El modelo y los resultados están descritos con detalle en el artículo del
proyecto y se validan contra la solución analítica de Erlang C con un
error inferior al 2,3 %.

## Estructura

```
.
├── index.html      # Página completa (HTML + CSS + JS)
└── README.md
```

## Licencia

Proyecto académico con fines educativos.
