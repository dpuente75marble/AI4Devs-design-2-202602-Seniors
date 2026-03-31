# Desglose técnico - US-03 (Análisis automático de CV con IA)

## Objetivo

Descomponer la User Story US-03 en tareas técnicas accionables para el equipo de desarrollo, incluyendo estimación en puntos Fibonacci.

---

## Ticket 1 - Subida y almacenamiento de CV

**Tipo:** Backend / Integración  
**Descripción:**  
Implementar subida de CV y almacenamiento en sistema externo (ej: S3).

**Criterios de aceptación:**

- El CV se almacena correctamente
- Se genera una URL accesible
- Se asocia a la Application

**Dependencias:** US-02  
**Estimación:** 3 puntos

---

## Ticket 2 - Servicio de procesamiento de CV

**Tipo:** Backend  
**Descripción:**  
Crear servicio que procese CVs de forma asíncrona.

**Criterios de aceptación:**

- El procesamiento se ejecuta en background
- Se maneja cola de tareas
- Se registra estado del proceso

**Dependencias:** Ticket 1  
**Estimación:** 5 puntos

---

## Ticket 3 - Integración con API de IA

**Tipo:** Backend / Integración  
**Descripción:**  
Integrar servicio de IA para extracción de información del CV.

**Criterios de aceptación:**

- Se envía el CV a la API
- Se recibe respuesta estructurada
- Se manejan errores de API

**Dependencias:** Ticket 2  
**Estimación:** 5 puntos

---

## Ticket 4 - Generación de scoring

**Tipo:** Backend  
**Descripción:**  
Implementar lógica para generar score del candidato.

**Criterios de aceptación:**

- Se calcula score basado en datos extraídos
- El score se almacena en Application
- Es configurable en futuro

**Dependencias:** Ticket 3  
**Estimación:** 3 puntos

---

## Ticket 5 - Persistencia de análisis

**Tipo:** Backend  
**Descripción:**  
Guardar resultados del análisis en base de datos.

**Criterios de aceptación:**

- Se guarda JSON estructurado
- Se relaciona con ApplicationAnalysis
- Se mantiene consistencia de datos

**Dependencias:** Ticket 3  
**Estimación:** 3 puntos

---

## Ticket 6 - Gestión de errores y fallback

**Tipo:** Backend  
**Descripción:**  
Gestionar errores en procesamiento de CV.

**Criterios de aceptación:**

- Se detectan errores de parsing o IA
- Se marca estado como error
- Se permite revisión manual

**Dependencias:** Ticket 3  
**Estimación:** 2 puntos

---

## Ticket 7 - Endpoint para consultar resultados

**Tipo:** Backend  
**Descripción:**  
Crear endpoint para consultar análisis de candidatos.

**Criterios de aceptación:**

- Endpoint GET disponible
- Devuelve score y datos estructurados
- Control de permisos

**Dependencias:** Ticket 5  
**Estimación:** 2 puntos

---

## Ticket 8 - Visualización en frontend

**Tipo:** Frontend  
**Descripción:**  
Mostrar score e información del análisis en UI.

**Criterios de aceptación:**

- Se muestra score del candidato
- Se visualizan datos relevantes
- UI clara y usable

**Dependencias:** Ticket 7  
**Estimación:** 3 puntos

---

## Ticket 9 - Testing básico

**Tipo:** QA  
**Descripción:**  
Validar funcionamiento del flujo completo.

**Criterios de aceptación:**

- Flujo completo validado
- Casos de error comprobados
- Sin errores críticos

**Dependencias:** Todos  
**Estimación:** 2 puntos

---

## Resumen de estimación

Total: **28 puntos**
