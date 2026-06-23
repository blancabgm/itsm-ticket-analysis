# Dashboard y KPIs – ITSM Ticket Analysis (Caso 3)

Este documento recoge la definición de los KPIs, las medidas DAX y la estructura del dashboard desarrollado en Power BI para el Caso 3.  
El objetivo es proporcionar una visión clara del rendimiento del proceso ITSM durante 2023 y facilitar la toma de decisiones operativas.

---

## 1. KPIs principales del dashboard

El dashboard incluye los siguientes indicadores clave:

- **Total Tickets:** 2.330  
- **Avg Resolution Hours:** 11,43 h  
- **Avg First Response Hours:** 0,15 h  
- **SLA Resolution OK %:** 100%  
- **SLA First Response OK %:** 99,9%  

Estos KPIs permiten evaluar:

- la carga operativa del servicio,  
- la rapidez de respuesta,  
- la eficiencia en la resolución,  
- y el cumplimiento de los acuerdos de nivel de servicio (SLA).

---

## 2. Medidas DAX utilizadas

A continuación se documentan las medidas DAX principales utilizadas en el modelo.

---

### 2.1 Tiempo medio de resolución

```text
Avg Resolution Hours =
AVERAGEX(
    FILTER(
        'Tickets',
        NOT(ISBLANK('Tickets'[Resolution_Duration_Hours]))
    ),
    'Tickets'[Resolution_Duration_Hours]
)
```

---

### 2.2 Tiempo medio de primera respuesta
```text
Avg First Response Hours =
AVERAGEX(
    FILTER(
        'Tickets',
        NOT(ISBLANK('Tickets'[FirstResponse_Duration_Hours]))
    ),
    'Tickets'[FirstResponse_Duration_Hours]
)
```

---

### 2.3 SLA de resolución OK %
```text
SLA Resolution OK % =
DIVIDE(
    CALCULATE(COUNTROWS('Tickets'), 'Tickets'[Check_SLA_Resolution] = "OK"),
    CALCULATE(COUNTROWS('Tickets'), NOT(ISBLANK('Tickets'[SLA For Resolution])))
)
```

---

### 2.4 SLA de primera respuesta OK %
```text
SLA First Response OK % =
DIVIDE(
    CALCULATE(COUNTROWS('Tickets'), 'Tickets'[Check_SLA_FirstResponse] = "OK"),
    CALCULATE(COUNTROWS('Tickets'), NOT(ISBLANK('Tickets'[SLA For first response])))
)
```

---

### 2.5 Tickets por país
```text
Tickets by Country =
COUNTROWS('Tickets')
```
(Se utiliza segmentado por la columna Country.)

---

### 2.6 Tickets por prioridad
```text
Tickets by Priority =
COUNTROWS('Tickets')
```
(Se utiliza segmentado por la columna Priority.)

---

## 3. Estructura del modelo en Power BI
El modelo se basa en una única tabla principal:

- Tickets  
  Contiene toda la información del proceso ITSM:

    - fechas del ciclo de vida del ticket
    - SLA
    - agente asignado
    - país
    - prioridad
    - coordenadas
    - duraciones calculadas
    - validaciones de SLA
    - resultados de encuesta

Columnas calculadas clave:

- Resolution_Duration_Hours
- FirstResponse_Duration_Hours
- Latitude_fixed
- Longitude_fixed
- Check_SLA_Resolution
- Check_SLA_FirstResponse

---

## 4. Diseño del dashboard
El dashboard está organizado en una única página con:

## 4.1 Zona de KPIs
- Total Tickets
- Avg Resolution Hours
- Avg First Response Hours
- SLA Resolution OK %
- SLA First Response OK %

## 4.2 Gráficos principales
- Tickets por país (bar chart)
- Tickets por prioridad (donut chart)
- Evolución mensual (column chart)
- Mapa geográfico (usando Latitude_fixed y Longitude_fixed)

### 4.3 Filtros
- País
- Prioridad
- Estado
- Agente
- SLA

---

## 5. Conclusión técnica
El dashboard proporciona una visión clara y accionable del rendimiento del proceso ITSM durante 2023.
Las medidas DAX y las columnas calculadas permiten:

- validar la coherencia del proceso,
- medir tiempos reales,
- evaluar el cumplimiento de SLA,
- y analizar la distribución operativa del servicio.

El archivo .pbix está disponible en:

> powerbi/ITSM Ticket Analysis – Caso 3 .pbix

