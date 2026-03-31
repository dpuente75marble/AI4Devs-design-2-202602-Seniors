# User Stories iniciales - LTI

## Contexto

Este documento forma parte de la evolución del PRD generado en el módulo anterior.

El producto definido es LTI, una plataforma ATS (Applicant Tracking System) AI-native orientada a optimizar procesos de selección mediante automatización, scoring de candidatos y colaboración entre recruiters y hiring managers.

Para la definición de las User Stories y el backlog se han tomado como base:

- Funcionalidades clave definidas en el PRD
- Casos de uso principales
- Modelo de datos inicial
- Arquitectura de alto nivel

Repositorio del PRD base:
https://github.com/dpuente75marble/AI4Devs-design-1-202602-Seniors/blob/feature/lti-ddlp/lti/ddlp/LTI-iniciales.md

## Scope de esta iteración (MVP)

Este backlog se centra en una primera iteración del producto (MVP), priorizando:

- Creación y gestión de vacantes
- Recepción y visualización de candidaturas
- Evaluación inicial con soporte de IA
- Colaboración básica entre recruiters

Quedan fuera de alcance en esta fase:

- Integraciones con job boards externos
- Automatización avanzada de decisiones
- Analítica avanzada

## User Stories

### US-01 - Crear una vacante

**Historia de usuario**  
Como recruiter,  
quiero crear una vacante con la información principal del puesto,  
para iniciar un nuevo proceso de selección de forma estructurada.

**Criterios de aceptación**

**Escenario 1 - Creación correcta de la vacante**  
Dado que soy un recruiter autenticado,  
cuando completo los campos obligatorios de la vacante y guardo la información,  
entonces el sistema crea la vacante con estado "draft" y la muestra en mi listado de vacantes.

**Escenario 2 - Validación de campos obligatorios**  
Dado que estoy creando una vacante,  
cuando intento guardar el formulario sin informar uno o más campos obligatorios,  
entonces el sistema muestra mensajes de validación claros y no permite guardar la vacante.

**Escenario 3 - Edición antes de publicación**  
Dado que he creado una vacante en estado "draft",  
cuando accedo de nuevo a su detalle y modifico su información,  
entonces el sistema guarda los cambios y mantiene la vacante actualizada sin publicarla automáticamente.

**Notas adicionales**

- Campos mínimos sugeridos: título del puesto, departamento, ubicación, tipo de contrato, descripción y requisitos.
- La vacante debe quedar inicialmente en estado `draft`.
- Esta historia es base para el resto del flujo del MVP.

**Evaluación INVEST**

- **Independent**: sí, puede implementarse sin depender del resto de historias del pipeline.
- **Negotiable**: sí, los detalles del formulario pueden ajustarse durante refinamiento.
- **Valuable**: sí, aporta valor directo al recruiter al iniciar el proceso.
- **Estimable**: sí, el alcance es entendible y estimable.
- **Small**: sí, es abordable en una iteración.
- **Testable**: sí, los criterios de aceptación son verificables.

### US-02 - Recepción de candidaturas

**Historia de usuario**  
Como candidato,  
quiero poder aplicar a una vacante enviando mi CV,  
para participar en el proceso de selección.

**Criterios de aceptación**

**Escenario 1 - Aplicación exitosa**  
Dado que accedo a una vacante publicada,  
cuando completo el formulario de candidatura y adjunto mi CV,  
entonces el sistema registra mi candidatura y la asocia a la vacante correspondiente.

**Escenario 2 - Validación de información requerida**  
Dado que estoy aplicando a una vacante,  
cuando intento enviar la candidatura sin completar los campos obligatorios,  
entonces el sistema muestra mensajes de error y no permite enviar la solicitud.

**Escenario 3 - Confirmación al candidato**  
Dado que he enviado correctamente mi candidatura,  
cuando se registra en el sistema,  
entonces recibo una confirmación de que mi candidatura ha sido recibida.

**Notas adicionales**

- Campos mínimos: nombre, email, CV adjunto.
- El CV debe almacenarse de forma segura.
- Se debe crear una entidad `Application` asociada a `Candidate` y `JobPosition`.

**Evaluación INVEST**

- **Independent**: sí, puede implementarse independientemente del pipeline.
- **Negotiable**: sí, el formulario puede evolucionar.
- **Valuable**: sí, permite la entrada de candidatos al sistema.
- **Estimable**: sí, el alcance es claro.
- **Small**: sí, es implementable en un sprint.
- **Testable**: sí, los escenarios son verificables.

### US-03 - Análisis automático de CV con IA

**Historia de usuario**  
Como recruiter,  
quiero que el sistema analice automáticamente los CVs recibidos,  
para obtener información estructurada y un scoring inicial de los candidatos.

**Criterios de aceptación**

**Escenario 1 - Extracción de información del CV**  
Dado que un candidato ha enviado su CV,  
cuando el sistema procesa el documento,  
entonces extrae información relevante como nombre, experiencia, habilidades y formación.

**Escenario 2 - Generación de scoring inicial**  
Dado que el CV ha sido procesado,  
cuando el sistema analiza la información extraída,  
entonces asigna un score inicial basado en criterios definidos (skills, experiencia, etc.).

**Escenario 3 - Persistencia de resultados**  
Dado que el CV ha sido analizado,  
cuando finaliza el procesamiento,  
entonces los datos estructurados y el score quedan almacenados en el sistema.

**Escenario 4 - Gestión de errores**  
Dado que el CV no puede ser procesado correctamente,  
cuando ocurre un error en el análisis,  
entonces el sistema registra el error y marca la candidatura como pendiente de revisión manual.

**Notas adicionales**

- Uso de LLM para parsing de CV.
- Generación de JSON estructurado.
- Score inicial basado en reglas simples o IA.
- Preparado para evolución futura a ranking avanzado.

**Evaluación INVEST**

- **Independent**: sí, desacoplado del resto del pipeline.
- **Negotiable**: sí, el modelo y criterios pueden evolucionar.
- **Valuable**: sí, reduce trabajo manual del recruiter.
- **Estimable**: sí, se puede dividir en parsing + scoring.
- **Small**: medio, pero abordable en un sprint.
- **Testable**: sí, con validación de outputs estructurados.

### US-04 - Visualización de candidatos en pipeline

**Historia de usuario**  
Como recruiter,  
quiero visualizar los candidatos en un pipeline por estados,  
para gestionar el proceso de selección de forma clara y organizada.

**Criterios de aceptación**

**Escenario 1 - Visualización del pipeline**  
Dado que accedo a una vacante,  
cuando entro en la vista de candidatos,  
entonces veo un pipeline organizado por estados (ej: aplicado, en revisión, entrevista, oferta).

**Escenario 2 - Movimiento de candidatos entre estados**  
Dado que estoy gestionando candidatos,  
cuando arrastro un candidato a otro estado,  
entonces el sistema actualiza su estado correctamente.

**Escenario 3 - Persistencia de cambios**  
Dado que he cambiado el estado de un candidato,  
cuando refresco la página o vuelvo a entrar,  
entonces el candidato mantiene su nuevo estado.

**Escenario 4 - Visualización de información básica**  
Dado que estoy viendo el pipeline,  
cuando visualizo un candidato,  
entonces veo información clave como nombre, score y posición actual.

**Notas adicionales**

- UI tipo kanban.
- Estados configurables.
- Integración con datos de Application.
- Mostrar score generado por IA.

**Evaluación INVEST**

- **Independent**: sí, aunque usa datos previos, no depende funcionalmente.
- **Negotiable**: sí, diseño y estados pueden cambiar.
- **Valuable**: sí, mejora la gestión del recruiter.
- **Estimable**: sí, frontend + backend claros.
- **Small**: sí, MVP del pipeline es abordable.
- **Testable**: sí, mediante validación de estados y persistencia.

### US-05 - Registro de feedback estructurado

**Historia de usuario**  
Como hiring manager,  
quiero registrar feedback estructurado sobre un candidato,  
para colaborar con el recruiter en la toma de decisiones del proceso.

**Criterios de aceptación**

**Escenario 1 - Registro de feedback**  
Dado que estoy revisando un candidato,  
cuando completo y envío un formulario de evaluación,  
entonces el sistema guarda mi feedback asociado a esa candidatura.

**Escenario 2 - Visualización de feedback previo**  
Dado que existe feedback registrado sobre un candidato,  
cuando accedo a su detalle,  
entonces puedo consultar las evaluaciones realizadas previamente por otros usuarios autorizados.

**Escenario 3 - Validación de permisos**  
Dado que un usuario sin permisos intenta acceder al feedback,  
cuando intenta visualizar o registrar una evaluación,  
entonces el sistema deniega el acceso.

**Escenario 4 - Estructura común de evaluación**  
Dado que estoy completando una evaluación,  
cuando accedo al formulario,  
entonces veo campos estructurados como valoración general, comentarios, fortalezas y riesgos detectados.

**Notas adicionales**

- La evaluación debe quedar vinculada a `Application` y `User`.
- Se debe contemplar RBAC básico.
- Esta historia prepara el terreno para consolidación futura de feedback por IA.

**Evaluación INVEST**

- **Independent**: sí, puede implementarse como módulo separado.
- **Negotiable**: sí, la estructura del feedback puede ajustarse.
- **Valuable**: sí, aporta colaboración real al proceso.
- **Estimable**: sí, alcance funcional claro.
- **Small**: sí, viable para MVP.
- **Testable**: sí, con validación funcional y de permisos.
