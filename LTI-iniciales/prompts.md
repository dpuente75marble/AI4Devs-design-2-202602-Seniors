# Prompts utilizados

## Objetivo

En esta práctica se han utilizado varios prompts iterativos para transformar el PRD inicial de LTI en un backlog de producto priorizado, con User Stories bien definidas y una primera aproximación técnica para su implementación.

---

## Prompt 1 - Generación inicial de User Stories

Actúa como un Product Owner senior con experiencia en productos SaaS B2B y metodologías ágiles.

A partir del siguiente contexto de producto, genera 6 User Stories para un MVP.

El producto es LTI, una plataforma ATS (Applicant Tracking System) AI-native orientada a optimizar procesos de selección mediante automatización, scoring de candidatos y colaboración entre recruiters y hiring managers.

Ten en cuenta estas funcionalidades base:

- Creación de vacantes
- Recepción de candidaturas
- Pipeline visual
- Evaluación colaborativa
- Entrevistas
- IA para análisis y scoring de candidatos

Para cada User Story incluye:

- Título
- Historia en formato "Como / quiero / para"
- Breve descripción del valor aportado

### Resultado

Este prompt fue útil para obtener una primera lista de historias alineadas con el producto.

### Limitaciones

- Las historias iniciales eran demasiado generales
- Faltaban criterios de aceptación
- No quedaban suficientemente aterrizadas para desarrollo

---

## Prompt 2 - Mejora de User Stories con criterios INVEST y BDD

Actúa como un Product Owner senior y Business Analyst.

Toma las User Stories generadas previamente para LTI y mejóralas para que cumplan los criterios INVEST.

Para cada historia incluye:

- Título
- Historia en formato "Como / quiero / para"
- 3 o 4 criterios de aceptación en formato BDD (Dado / cuando / entonces)
- Evaluación breve contra INVEST

### Resultado

Este prompt mejoró mucho la calidad del backlog, porque transformó ideas generales en historias más claras, estimables y testeables.

### Limitaciones

- Seguía faltando contexto técnico
- Algunas historias necesitaban más detalle de datos y dependencias

---

## Prompt 3 - Priorización del backlog para MVP

Actúa como un Product Manager senior.

A partir de estas User Stories de LTI, genera una priorización del backlog para una primera iteración MVP.

Ten en cuenta:

- valor de negocio
- dependencias funcionales
- lógica de implementación
- impacto en el usuario
- diferenciación por uso de IA

Devuelve:

- orden recomendado de implementación
- justificación breve de cada prioridad

### Resultado

Este prompt permitió ordenar el backlog con una lógica coherente para una primera release.

### Limitaciones

- La priorización propuesta por IA necesitó revisión humana para asegurar consistencia con el flujo real del producto

---

## Prompt 4 - Desglose técnico en tickets de trabajo

Actúa como un Tech Lead con experiencia en diseño de producto y desarrollo de software.

Toma la siguiente User Story de LTI y desglósala en tickets de trabajo técnicos listos para sprint planning.

Incluye:

- título del ticket
- descripción
- tipo (frontend, backend, integración, QA, spike...)
- criterios de aceptación
- dependencias
- estimación en Fibonacci

La User Story es:
"Como recruiter, quiero que el sistema analice automáticamente los CVs recibidos, para obtener información estructurada y un scoring inicial de los candidatos."

### Resultado

Este prompt fue el más útil para aterrizar técnicamente una User Story y convertirla en trabajo real para el equipo.

### Limitaciones

- Requirió ajuste manual para evitar tickets demasiado amplios
- Algunas tareas técnicas debían dividirse mejor para encajar en un sprint

---

## Prompt ganador

El prompt más efectivo fue el **Prompt 4 - Desglose técnico en tickets de trabajo**.

### ¿Por qué fue el mejor?

- Fue el que más valor práctico aportó para pasar de definición funcional a ejecución
- Permitió convertir una User Story en trabajo accionable para un equipo de desarrollo
- Ayudó a aterrizar aspectos que normalmente quedan implícitos: integraciones, persistencia, errores, procesamiento asíncrono y validaciones
- Encaja directamente con la parte del ejercicio donde se pide generar tickets de trabajo

---

## Conclusiones

El uso de prompts iterativos fue más efectivo que intentar resolver todo con una sola instrucción.

### Aprendizajes principales

- Un primer prompt sirve para explorar
- Un segundo prompt sirve para refinar calidad
- Un tercero ayuda a priorizar
- Un cuarto convierte backlog en planificación real

La combinación de varios prompts permitió construir un backlog más sólido, claro y cercano a un contexto profesional real.
