# ITSM Ticket Analysis – Caso 3 (ITSM 2023) 📊

Análisis del rendimiento de un sistema ITSM durante 2023, con foco en:
- volumen de tickets,
- tiempos de primera respuesta y resolución,
- cumplimiento de SLA,
- distribución por país y prioridad.

Este proyecto combina **Data + Procesos + Calidad**, con especial énfasis en:
- evaluación de la calidad del dato (Data Quality),
- validación de reglas de proceso y SLA,
- diseño de un dashboard profesional en Power BI.

Este caso forma parte de un portfolio orientado a **Data + Procesos + Calidad**, con foco en la madurez del proceso ITSM y la coherencia del dato.

---

## 1. Objetivos

- Evaluar el rendimiento del proceso de gestión de tickets ITSM.
- Analizar la distribución de la carga operativa por país y prioridad.
- Medir tiempos de primera respuesta y resolución.
- Validar el cumplimiento de SLA y su coherencia con los datos.
- Proponer recomendaciones de mejora basadas en KPIs.

## 2. Estructura del repositorio
itsm-ticket-analysis/
├─ README.md
├─ data/
├─ powerbi/
├─ docs/
└─ assets/

- `data/` → dataset o enlace a la fuente.
- `docs/` → documentación técnica (Data Quality, SLA, KPIs, dashboard).
- `powerbi/` → archivo `.pbix` del dashboard.
- `assets/` → capturas del dashboard y gráficos clave.
- `notebooks/` (opcional) → análisis exploratorio adicional.

---

## 3. Dataset

- Origen: dataset de soporte técnico (ITSM).
- Registros: 2.331.
- Columnas: 28+
- Campos clave: estado, prioridad, fechas, SLA, agente, país, coordenadas.

> Nota: el dataset puede no estar incluido por licencia.  
> Se documenta la estructura y origen.

----

## 4. Documentación técnica

- `docs/01_data_quality.md` → reglas aplicadas, problemas detectados, correcciones.
- `docs/02_sla_logic.md` → lógica de SLA de resolución y primera respuesta.
- `docs/03_kpis_dashboard.md` → definición de KPIs y diseño del dashboard.

## 5. Herramientas

El dashboard incluye:

- KPIs principales (volumen, tiempos, SLA).  
- Distribución por país.  
- Distribución por prioridad.  
- Evolución mensual.  
- Filtros interactivos.  

Capturas disponibles en `/assets`.

---

##6. Herramientas utilizadas

- Power BI (modelo DAX, visualizaciones)
- Power Quaery (limpieza y preparación)
- Github + Notion (documentación)

---

## 6. Estado del proyecto

- ✅ Data Quality documentado.
- ✅ Lógica de SLA documentada.
- ✅ Dashboard en Power BI construido.
