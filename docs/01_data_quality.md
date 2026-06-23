# Data Quality – ITSM Ticket Analysis (Caso 3)

Este documento recoge el análisis completo de calidad del dato aplicado al dataset ITSM utilizado en el Caso 3. El objetivo es garantizar que los KPIs, conclusiones y visualizaciones del dashboard se basen en datos consistentes, completos y coherentes con el proceso ITSM.

---

## 1. Exploración inicial del dataset

- Registros: **2.331**
- Columnas: **21+**
- Columnas de fecha: Created time, Expected SLA to resolve, Expected SLA to first response, First response time, Resolution time, Close time
- Columnas categóricas: Status, Priority, Topic, Agent Group, Agent Name, Country, Product group, Support Level, Source, SLA For first response, SLA For Resolution
- Columnas numéricas: Ticket ID, Agent interactions, Survey results, Latitude, Longitude

### Observaciones iniciales

- Formato de fechas: `dd/mm/yyyy hh:mm:ss`
- Prioridades: High, Medium, Low
- Estados: Open, In progress, Resolved, Closed
- Países: UK, Germany, Italy, Poland, etc.

---

## 2. Reglas de calidad del dato aplicadas

### 2.1 Campos obligatorios

#### Regla 1 — Created time obligatorio
Todo ticket debe tener fecha de creación.

- Vacíos: 0  
- Porcentaje válido: 100%

**Conclusión:** El sistema ITSM genera correctamente el campo Created time.

---

#### Regla 7 — Prioridad siempre informada
Todos los tickets deben tener Priority.

- Vacíos: 0  
- Porcentaje válido: 100%

---

#### Regla 8 — Estado siempre informado
Todos los tickets deben tener Status.

- Vacíos: 0  
- Porcentaje válido: 100%

---

#### Regla 9 — Categoría siempre informada
Todos los tickets deben tener Topic.

- Vacíos: 0  
- Porcentaje válido: 100%

---

### 2.2 Coherencia entre estado y tiempos

#### Regla 2 — Status vs Resolution time
Si Status = Resolved o Closed → Resolution time no puede estar vacío.

- Tickets Resolved: 739  
- Resolution time vacío: 0  

**Conclusión:** Regla cumplida al 100%.

---

#### Regla 3 — Status vs Close time
Si Status = Closed → Close time no puede estar vacío.

- Tickets Closed: 1.173  
- Close time vacío: 0  

**Conclusión:** Regla cumplida al 100%.

---

### 2.3 Coherencia temporal

#### Regla 4 — Orden lógico de fechas
Created ≤ First response ≤ Resolution ≤ Close

Resultados:

- Created ≤ First response → OK: 2.310 | ERROR: 2 | BLANK: 18  
- First response ≤ Resolution → OK: 1.894 | ERROR: 18 | BLANK: 418  
- Resolution ≤ Close → OK: 1.131 | ERROR: 42 | BLANK: 1.157  

**Conclusión:** Existen incoherencias puntuales (errores de registro o zona horaria).

---

### 2.4 SLA de resolución y primera respuesta

#### Regla 5 — SLA de resolución coherente
Si SLA For Resolution = "Within SLA" → duración ≤ 24 h.

- Tickets Within SLA: 1.547  
  - OK: 1.546  
  - ERROR: 1  

**Conclusión:** 1 ticket inconsistente (SLA marcado como OK sin Resolution time).

---

#### Regla 6 — SLA de primera respuesta coherente
Si SLA For first response = "Within SLA" → duración 2 h.
- OK: todos  
- ERROR: 0  

**Conclusión:** SLA de primera respuesta completamente coherente.

---

### 2.5 Asignación de agente

#### Regla 10 — Agente o grupo asignado
Si Status ≠ Open → debe existir Agent Name o Agent Group.

- Tickets no Open: 2.312  
- Sin agente: 0  

**Conclusión:** No existen tickets sin responsable.

---

### 2.6 Coherencia geográfica

#### Regla 11 — País vs coordenadas
Las coordenadas deben estar dentro de rangos válidos.

Hallazgo:

- Parte del dataset tiene coordenadas correctas.
- Otra parte tiene valores escalados ×10.

Corrección aplicada:

```text
Latitude_fixed  = if Latitude  > 90  then Latitude  / 10 else Latitude
Longitude_fixed = if Longitude > 180 then Longitude / 10 else Longitude
´´´
Resultado:

100% de coordenadas dentro de rangos válidos.

---

## 3. Estado final del dataset
Tras aplicar todas las reglas y correcciones:

- Campos esenciales completos.
- Incoherencias temporales identificadas y documentadas.
- SLA validado con un único caso inconsistente.
- Coordenadas normalizadas.
- Dataset con nivel de calidad alto, apto para análisis y visualización.

---

## 4. Notas adicionales
- Las columnas originales de coordenadas se ocultaron para evitar confusión.
- Las columnas calculadas se utilizaron en Power BI para KPIs y validaciones.
- Los registros con incoherencias se marcaron para análisis posterior.
