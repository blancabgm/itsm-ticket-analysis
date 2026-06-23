# Reglas y Lógica de SLA – ITSM Ticket Analysis (Caso 3)

Este documento describe la lógica utilizada para validar el cumplimiento de los SLA de **resolución** y **primera respuesta** en el dataset ITSM del Caso 3.  
El objetivo es asegurar que los KPIs del dashboard reflejan correctamente el comportamiento real del proceso y que no existen inconsistencias entre los tiempos registrados y el estado del SLA.

---

## 1. SLA de resolución (Resolution SLA)

El SLA de resolución mide si un ticket se resolvió dentro del tiempo objetivo definido en `Expected SLA to resolve`.  
En este caso, el SLA teórico es de **24 horas**.

---

### 1.1 Cálculo del tiempo de resolución

Se creó la columna calculada:

```text
Resolution_Duration_Hours = Duration.Hours([Resolution time] - [Created time])
```

---

### 1.2 Lógica de calidación SLA

Se creo la columna de control:
```text
Check_SLA_Resolution =
if [SLA For Resolution] = "Within SLA"
   and (
        [Resolution_Duration_Hours] = null
        or [Resolution_Duration_Hours] > 24
   )
then "ERROR"
else "OK"
```
---

### 1.3 Resultados de la validación
Tickets con SLA For Resolution = "Within SLA": 1.547

OK: 1.546

ERROR: 1

Conclusión:  
Se detecta 1 ticket inconsistente, marcado como “Within SLA” sin Resolution time informado.
Este caso debe revisarse en origen o excluirse del cálculo del SLA.

---

## 2. SLA de primera respuesta (First Response SLA)
El SLA de primera respuesta mide si el ticket recibió una respuesta inicial dentro del tiempo objetivo definido en Expected SLA to first response.
En este caso, el SLA teórico es de 2 horas.

---

### 2.1 Cálculo del tiempo de primera respuesta
Se creó la columna calculada:
```text
FirstResponse_Duration_Hours = Duration.Hours([First response time] - [Created time])
```
---

### 2.2 Lógica de validación del SLA
Se creó la columna de control:
```text
Check_SLA_FirstResponse =
if [SLA For first response] = "Within SLA"
   and (
        [FirstResponse_Duration_Hours] = null
        or [FirstResponse_Duration_Hours] > 2
   )
then "ERROR"
else "OK"
```
---

### 2.3 Resultados de la validación
Tickets con SLA For first response = "Within SLA": (total del modelo)

OK: todos

ERROR: 0

Conclusión:  
El SLA de primera respuesta es completamente coherente con los tiempos registrados.
No se detectan inconsistencias.

---

## 3. Incoherencias detectadas
1 ticket con SLA de resolución inconsistente.

Ningún caso incorrecto en SLA de primera respuesta.

Recomendación: revisar el ticket inconsistente en origen o excluirlo del cálculo del SLA.

---

## 4. Conclusión técnica
El análisis de SLA confirma que:

El SLA de primera respuesta es altamente consistente.

El SLA de resolución presenta solo un caso aislado de inconsistencia.

El modelo de SLA es fiable y adecuado para análisis operativo y visualización en Power BI.

Estado final:  
Las reglas de SLA están correctamente aplicadas y documentadas.
Los KPIs derivados son válidos y representativos del proceso ITSM.
