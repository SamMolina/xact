# Entrevista Técnica: Jefe de Plataforma — Ejemplo de entrevista

> **Tipo de documento:** Ejemplo de guion de entrevista (assessment).
>
> Este documento es un **ejemplo de entrevista** para conducir una conversación de evaluación con el **jefe de la plataforma OBS** y sus líderes técnicos. No es un cuestionario de respuesta cerrada: las preguntas son **abiertas** y buscan que la persona entrevistada describa, con ejemplos concretos y datos, cómo opera hoy la plataforma a nivel técnico y de procesos.
>
> **Cómo usar esta guía:**
> - Recorre las subdimensiones en orden; cada una abre con su objetivo de evaluación.
> - Usa los criterios como bloques temáticos y las preguntas como disparadores de conversación.
> - Profundiza con repreguntas ("¿puedes darme un ejemplo?", "¿qué porcentaje?", "¿con qué frecuencia?", "¿cuánto tiempo les ahorra?") para obtener evidencia, no solo percepciones.
> - El objetivo es entender la estrategia de la plataforma, mapear su estrategia de calidad, sus formas de trabajo (WoW), herramientas y métricas, y valorar la eficiencia de ingeniería como apalancamiento (impacto producido ÷ tiempo invertido) para el negocio.

| Nivel | Elemento | Descripción |
|-------|----------|-------------|
| 1.º | Subdimensión | Área temática que se explora durante la entrevista |
| 2.º | Criterio | Bloque de preguntas dentro de una subdimensión |
| 3.º | Pregunta | Pregunta abierta para guiar la conversación |

---

## Subdimensión 1: Estabilidad de Producto y Plataforma

El objetivo aquí es evaluar qué tan estable, resiliente y predecible es la plataforma OBS en producción: si la organización opera con datos, forecasting y automatización, o reacciona a los incidentes a mano. Buscamos entender cuánto apalancamiento generan sus prácticas de estabilidad frente al esfuerzo operativo que consumen.

### Criterio 1.1: Disponibilidad y Resiliencia

- **Disponibilidad:** ¿Cómo miden hoy la disponibilidad de la plataforma y la frecuencia de incidentes de alta prioridad? ¿Cuánto histórico de downtime y de patrones de uso pico tienen tomado y benchmarkeado (un trimestre, 2-3 trimestres, varios años)? ¿Qué mecanismos de failover, DR y BCP tienen en marcha, con qué frecuencia hacen drills, y cuánto trabajo manual les cuesta sostener esa resiliencia? ¿Han llegado a prácticas de chaos engineering o herramientas AIOps que reduzcan ese esfuerzo?

### Criterio 1.2: Indicadores de Éxito y Forecasting

- **Indicadores de éxito:** ¿Qué métricas de producto y de entrega siguen hoy (frecuencia de despliegue, lead time para cambios, disponibilidad, latencia, performance) y desde cuándo tienen histórico? ¿Hacen forecasting de la demanda y los indicadores de negocio — con qué horizonte (≤1 trimestre, 4-6, 6-8) y qué tan precisos resultan frente a la realidad? Cuéntame una decisión concreta que hayan tomado a partir de esos datos: ¿qué cambió y cuánto impacto tuvo?

### Criterio 1.3: Infraestructura

- **Infraestructura:** ¿Cuál es su estrategia de infraestructura para los próximos 3-4 años (on-prem, híbrida, cloud, multi-cloud)? ¿Qué tan extendida está la infraestructura como código (IaC) y cuánto del aprovisionamiento de recursos es automatizado vs. manual? ¿Tienen pipelines de canary y estrategias de rollback, y deciden cuándo y dónde escalar capacidad por modelos/forecasting o por intuición? ¿Cuánto tiempo de ingeniería les libera esa automatización?

### Criterio 1.4: Calidad

- **Calidad:** ¿Cómo gestionan hoy las vulnerabilidades de seguridad, la deuda técnica y la consistencia de datos en la plataforma? ¿Tienen un plan de remediación de vulnerabilidades que se siga de forma sostenida, scanners integrados en el pipeline, y una estrategia para pagar tech debt sin necesidad de "sprints de deuda" dedicados? Dame un ejemplo de cómo priorizan: ¿qué tanto retrabajo o riesgo evitan al resolver estos temas temprano frente a dejarlos acumular?

## Subdimensión 2: Excelencia en Ingeniería

Esta subdimensión evalúa la disciplina y las prácticas de ingeniería de los equipos de la plataforma a lo largo del ciclo de vida —desde el análisis de requisitos hasta el despliegue y los requisitos transversales— para entender si maximizan la velocidad de iteración y el aprendizaje, o si pierden tiempo en fricción, retrabajo y dependencias.

### Criterio 2.1: Análisis de Requisitos

- **Análisis de requisitos:** ¿Cómo levantan y detallan los requisitos antes de construir? ¿Qué tan consistentes y de alta calidad son, capturan y actualizan los requisitos no funcionales (NFRs), evalúan soluciones alternativas y valoran el valor de negocio de cada solución antes de comprometerse? ¿Cuánto retrabajo evitan al validar esto temprano?
- **Diseño de requisitos:** ¿Cuentan con un diseño detallado del estado futuro, los user journeys y los flujos de proceso? ¿Qué tan vigentes están — se actualizan con regularidad y se usan activamente en las discusiones, o quedan obsoletos y nadie los consulta?

### Criterio 2.2: Arquitectura y Diseño

- **Engagement de arquitectura:** ¿Tienen una architecture runway y CFRs definidos antes de desarrollar? ¿Crean diagramas y modelos (p. ej. C4) que estén disponibles y sean fáciles de encontrar para todos, identifican y priorizan deuda técnica de arquitectura de forma regular, y hay suficiente documentación o sesiones para que los equipos compartan la visión, o trabajan en silos?
- **Documentación:** ¿Cómo capturan las decisiones técnicas (p. ej. ADRs) y la documentación funcional? ¿El sistema genera especificaciones vivas a partir de tests bien descritos, y la documentación está estandarizada y centralizada para ser consumida, o está dispersa y se desactualiza? ¿Cuánto tiempo pierden hoy buscando o reconstruyendo ese conocimiento?

### Criterio 2.3: Desarrollo

- **Disciplina de desarrollo:** Descríbeme el flujo de trabajo de un desarrollador: ¿corren linting y secret scanning localmente (p. ej. via pre-commit hooks) o solo en el pipeline? ¿Siguen prácticas XP, escriben tests efectivos con el dataset correcto, identifican y **toman** la deuda técnica en cada iteración, hacen refactoring y mockean dependencias externas para no frenarse? ¿Qué tan corto es el ciclo de feedback que esto les da?
- **Onboarding y cultivo de desarrolladores:** Cuando entra un desarrollador nuevo, ¿cuánto tarda en tener su entorno listo y productivo (minutos, horas, días)? ¿El onboarding está estandarizado y guiado por checklists con scripts automatizados, y existen sesiones/documentos sobre el dominio, el panorama general y seguridad, o cada quien arma su setup a su manera?
- **Prácticas de control de fuentes:** ¿Cómo gestionan ramas y commits? ¿Usan trunk-based development con feature toggles, commits atómicos, trazables a la historia y con estándares de la organización, o manejan múltiples ramas con mucho esfuerzo de merge y commits poco trazables?
- **Prácticas de gestión de datos:** ¿Cómo manejan los cambios de base de datos? ¿Las migraciones se capturan como código y se versionan, los backups se toman y se prueban periódicamente, y el monitoreo tiene alertas habilitadas, o los cambios se hacen ad-hoc por la GUI y reaccionan a mano?

### Criterio 2.4: Despliegue

- **Pipeline:** ¿Cómo es su pipeline de build y despliegue? ¿Está automatizado el build (CI) y el despliegue (CD), con suites de pruebas en varios niveles, monitoreo y alertas para detectar fallos temprano, y security scanners? ¿Cada commit puede ir a producción, solo commits seleccionados, o todavía crean y despliegan artefactos manualmente?
- **Prácticas de cloud:** ¿Sus componentes están contenedizados y desacoplados, escalan horizontalmente con facilidad, y la infraestructura está como código con configuraciones y políticas (escalado, logs) optimizadas — o la infra se crea manualmente una vez y nunca se ajusta? ¿Cuánto esfuerzo operativo les ahorra (o cuesta) ese modelo hoy?

### Criterio 2.5: Aseguramiento de Calidad

- **Testing shift-left / calidad:** ¿Cómo aplican la pirámide de pruebas? ¿Cubren todos los niveles con tests efectivos y el dataset correcto en cada capa, tienen entorno de pruebas disponible, automatización y mocks de servicios externos en ambientes bajos para cubrir todos los escenarios — o las pruebas son ad-hoc, sin estrategia y con dependencias que hacen el sistema no testeable? ¿Qué tan temprano detectan los defectos con este enfoque?

### Criterio 2.6: CFRs (Requisitos Transversales)

- **Accesibilidad:** ¿Existe una guía de accesibilidad estándar y qué tan consistentemente la siguen los equipos en la implementación? ¿Todas las soluciones desarrolladas cumplen los requisitos de accesibilidad definidos, solo algunas, o no se considera el aspecto?
- **Logging:** ¿Los niveles y patrones de logs están estandarizados? ¿Pueden trazar una petición o acción de extremo a extremo a través de los sistemas usando correlation ids, parcialmente, o los logs se usan de forma aleatoria y nada es trazable?

## Subdimensión 3: DevOps

Esta subdimensión evalúa la madurez de las prácticas DevOps de la plataforma: integración y despliegue continuo, operaciones en producción y gestión de entornos. El foco es la velocidad de iteración, la baja fricción para liberar valor y la minimización de la carga operativa.

### Criterio 3.1: Integración y Despliegue Continuo

- **Build:** ¿Dónde ocurren los check-ins y con qué frecuencia integran a la mainline (semanas/meses, cada pocos días, o integración verdaderamente continua sobre mainline)? ¿El proceso de build incluye una buena mezcla de tests (unitarios, integración, contrato, funcionales, aceptación) mayormente verdes, cuánto testing manual siguen necesitando para certificar calidad, y qué pasa cuando un build queda rojo — quién es dueño y cuánto tarda en arreglarse?
- **Despliegue:** ¿Con qué frecuencia despliegan a producción (mensual o menos, casi diario, varias veces al día bajo demanda)? ¿El despliegue es automatizado y con cero downtime (blue-green, canary, rolling), quién decide cuándo se libera — el negocio o restricciones de TI — y existen congelamientos preventivos en periodos pico? Dame un ejemplo de un despliegue reciente de punta a punta.

### Criterio 3.2: Operaciones de Producción

- **Observabilidad:** ¿Qué patrones de observabilidad usan (agregación de logs, trazas distribuidas, health checks, alerting, APM)? ¿Se usan de forma esporádica por equipos individuales, están documentados, estandarizados en su implementación, o además probados para cumplir los SLAs? ¿Qué tan rápido detectan y diagnostican un problema antes de que el usuario lo note?
- **Continuidad de negocio:** ¿Cómo está diseñada la continuidad de la plataforma? ¿Operan en activo-pasivo y, en ese caso, cuál es su MTTR real (más de 24h, 12-24h, 6-12h, 2-6h), o ya están en activo-activo con cero downtime?

### Criterio 3.3: Entornos

- **Aprovisionamiento y uso:** ¿Cómo aprovisionan los entornos? ¿Son servidores bare metal o VMs de larga vida provisionados manualmente, VMs programáticas y mutables, o contenedores/funciones serverless efímeros e inmutables provisionados por código? ¿Cuánto tiempo y esfuerzo manual les toma levantar o replicar un entorno?
- **Buenas prácticas:** ¿Cómo manejan la configuración, los feature toggles y los secrets? ¿La configuración está externalizada del artefacto con un método consistente y trazable a un check-in, los toggles se definen a nivel de feature de negocio, y los secrets se gestionan en un servidor de secrets — o todo está embebido en el artefacto y requiere rebuilds y manejo manual?

## Cierre: Mapeo de dolores

> Bloque de síntesis (no puntuado). Úsalo al final para consolidar y priorizar los dolores detectados a lo largo de la entrevista.

- **Principales dolores:** De todo lo que conversamos —estabilidad y resiliencia de la plataforma, indicadores y forecasting, infraestructura y calidad; las prácticas de ingeniería (requisitos, arquitectura, desarrollo, despliegue, QA y CFRs); y DevOps (CI/CD, operaciones y entornos)—, ¿cuáles son los **3 dolores** que más les frenan hoy? Para cada uno, ¿qué impacto tiene (tiempo perdido, defectos, retrabajo, riesgo) y qué tan grande sería el apalancamiento de resolverlo frente al esfuerzo que implica?
