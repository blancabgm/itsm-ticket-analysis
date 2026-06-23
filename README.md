# ITSM Ticket Analysis – Caso 3 (ITSM 2023) 📊

Este proyecto analiza el rendimiento de un sistema ITSM durante 2023, combinando **Data Quality + análisis de proceso + visualización en Power BI** para evaluar la madurez del proceso y el cumplimiento de SLA.

---

## 1. Objetivos del proyecto

- Evaluar el rendimiento del proceso ITSM durante 2023.  
- Analizar volumen, prioridades, países y tiempos del ciclo.  
- Validar el cumplimiento de SLA y su coherencia con los datos.  
- Identificar oportunidades de mejora basadas en KPIs.  
- Diseñar un dashboard profesional en Power BI.

---

## 2. Estructura del repositorio
itsm-ticket-analysis-caso3/
├─ README.md
├─ data/
├─ powerbi/
│  └─ ITSM_Ticket_Analysis_Caso3.pbix
├─ docs/
│  ├─ 01_data_quality.md
│  ├─ 02_sla_logic.md
│  └─ 03_dashboard_kpis.md
└─ assets/

- **data/** → dataset o enlace a la fuente.  
- **powerbi/** → archivo `.pbix` del dashboard.  
- **docs/** → documentación técnica (Data Quality, SLA, KPIs).  
- **assets/** → capturas del dashboard (se añadirán al final).

---

## 3. Dataset

- Registros: 2.331  
- Columnas: 20+  
- Campos clave: estado, prioridad, fechas, SLA, agente, país, coordenadas.  

> Nota: el dataset puede no estar incluido por licencia.  
> Se documenta la estructura y origen.

----

## 4. Documentación técnica

- `docs/01_data_quality.md` → Reglas aplicadas, problemas detectados, correcciones.  
- `docs/02_sla_logic.md` → Lógica de SLA de resolución y primera respuesta.  
- `docs/03_dashboard_kpis.md` → KPIs, medidas DAX y estructura del dashboard.

---

## 5. Herramientas

El archivo de Power BI está disponible en:
- `powerbi/ITSM Ticket Analysis – Caso 3 .pbix`. 

El dashboard incluye:

- KPIs principales (volumen, tiempos, SLA).  
- Distribución por país.  
- Distribución por prioridad.  
- Evolución mensual.
- Mapageográfico.
- Filtros interactivos.

### Capturas del dashboard

- Vista general: `assets/dashboard_overview.png`  
- KPIs principales: `assets/dashboard_kpis.png`  
- Tickets por país: `assets/tickets_by_country.png`  
- Tickets por prioridad: `assets/tickets_by_priority.png`

---

##6. Herramientas utilizadas

- Power BI (modelo DAX, visualizaciones)
- Power Quaery (limpieza y preparación)
- Github + Notion (documentación)

---

## 7. Estado del proyecto

- ✔ Data Quality documentado  
- ✔ Lógica de SLA documentada  
- ✔ Dashboard construido  
- ✔ PBIX subido  
- 🔄 Pendiente de subir capturas del dashboard  
- 🔄 Pendiente de revisión final del dashboard (alineación visual y filtros)

---

## 8. Notion

La versión ejecutiva del caso está disponible en [Notion.] (https://app.notion.com/p/ITSM-Ticket-Analysis-Caso-3-ITSM-2023-38861cbed097806a883ff47ab947eef9?source=copy_link)
