# Entrevista Gerente de Desarrollo — Ejemplo de entrevista

> **Tipo de documento:** Ejemplo de guion de entrevista (assessment).
>
> Este documento es un **ejemplo de entrevista** diseñado para conducir una conversación de evaluación con un **Gerente de Desarrollo**. No es un cuestionario de respuesta cerrada: las preguntas son **abiertas** y buscan el **punto de vista gerencial** —estrategia, organización de equipos, métricas, priorización y decisiones técnicas que impactan al negocio—, sin entrar en un nivel de detalle técnico profundo.
>
> **Cómo usar esta guía:**
> - Recorre las subdimensiones en orden; cada una abre con su objetivo de evaluación.
> - Usa los criterios como bloques temáticos y las preguntas como disparadores de conversación.
> - Profundiza con repreguntas ("¿puedes darme un ejemplo?", "¿qué porcentaje?", "¿con qué frecuencia?", "¿quién lo decide?", "¿cuánto tiempo les ahorra?", "¿qué trabajo manual eliminó?") para obtener evidencia, no solo percepciones.
> - Las preguntas están planteadas bajo la óptica de **ingeniería efectiva** ("The Effective Engineer", Edmond Lau): efectividad = **impacto ÷ tiempo (apalancamiento)**. No basta con saber si una práctica o herramienta existe; interesa cuánto apalancamiento genera —velocidad de iteración, aprendizaje, priorización del trabajo de alto impacto, métricas que guían decisiones y reducción de carga operativa.
> - El objetivo es entender la estrategia y organización del área, las interacciones con otras áreas, las métricas de éxito, el cumplimiento (compliance) en el desarrollo, los principales desafíos, el manejo de prioridades, cómo se toman las decisiones técnicas que impactan al negocio y la eficiencia (apalancamiento) en ingeniería.

| Nivel | Elemento | Descripción |
|-------|----------|-------------|
| 1.º | Subdimensión | Área temática que se explora durante la entrevista |
| 2.º | Criterio | Bloque de preguntas dentro de una subdimensión |
| 3.º | Pregunta | Pregunta abierta para guiar la conversación |

---

## Subdimensión 1: Excelencia en Ingeniería (Prácticas de Ingeniería)

El objetivo es entender, desde la mirada gerencial, cómo están organizadas y estandarizadas las prácticas de ingeniería —desde el análisis de requisitos hasta el despliegue y la calidad— y cómo habilitan la eficiencia y la entrega de valor al negocio.

### Criterio 1.1: Análisis de Requisitos

- **Análisis de requisitos:** ¿Cómo se asegura tu área de que los requisitos lleguen a los equipos completos y con calidad? Cuéntame en qué medida se capturan los requisitos no funcionales (seguridad, rendimiento, cumplimiento), si se comparan soluciones alternativas y si se evalúa el valor de negocio antes de comprometer un desarrollo. Desde el apalancamiento: ¿cuánto retrabajo o desperdicio evita validar bien los requisitos al inicio frente a descubrir los problemas en construcción? ¿Puedes darme un ejemplo reciente?
- **Diseño de requisitos:** ¿Antes de construir existen diseños del estado futuro, recorridos de usuario y flujos de proceso documentados? ¿Se mantienen actualizados y se usan activamente en las discusiones, o tienden a quedar obsoletos y a perder relevancia? ¿Qué tanto aceleran la iteración y el aprendizaje del equipo al permitir validar ideas temprano, en lugar de convertirse en documentación que nadie consulta?

### Criterio 1.2: Arquitectura y Diseño

- **Involucramiento de arquitectura:** ¿Cómo gestionan la arquitectura como insumo para los equipos? ¿Existen diagramas y modelos (p. ej. C4) accesibles para todos, se identifica y prioriza la deuda técnica de arquitectura de forma regular, y hay espacios (sesiones, documentación) para que el equipo entienda el panorama completo, o se trabaja en silos? ¿Cómo priorizan qué deuda atacar primero según su impacto en la velocidad del negocio frente al esfuerzo de resolverla?
- **Documentación:** ¿Cómo se capturan y conservan las decisiones técnicas importantes (p. ej. ADRs)? ¿La documentación funcional está estandarizada y centralizada para que el equipo la encuentre con facilidad, o está dispersa y se desactualiza rápido? ¿Cuánto tiempo de búsqueda, retrabajo o decisiones repetidas les ahorra hoy esa documentación?

### Criterio 1.3: Desarrollo

- **Disciplina de desarrollo:** ¿Qué prácticas de ingeniería son estándar en tus equipos (revisiones de código, validaciones automáticas antes de subir cambios, pruebas)? ¿La deuda técnica se identifica y se atiende en cada iteración o se posterga? ¿El equipo refactoriza como parte normal del trabajo? ¿Cuánto acortan estas prácticas el ciclo de feedback y cuánto trabajo manual o defectos en producción evitan?
- **Onboarding y desarrollo de personas:** Cuando entra un nuevo desarrollador, ¿cuánto tarda en ser productivo y qué tan estandarizado/automatizado está ese proceso? ¿Cómo transmiten el conocimiento del dominio y la conciencia de seguridad al equipo? Como inversión de largo plazo, ¿cuánto tiempo del equipo libera un onboarding ágil frente al costo de acompañar a cada persona de forma manual?
- **Control de versiones:** ¿Qué tan estandarizada está la forma de trabajar con el código entre equipos (estrategia de ramas, integración, trazabilidad de los cambios hacia las historias)? ¿Esto genera fricción o reprocesos de integración que afecten la velocidad? ¿Cuánto tiempo se pierde en resolver conflictos o integraciones tardías que un flujo más estandarizado podría eliminar?
- **Gestión de datos:** ¿Cómo gestionan los cambios a bases de datos y la continuidad de los datos (cambios versionados como código, respaldos probados, monitoreo y alertas)? ¿Qué tanta visibilidad y control gerencial tienes sobre ese riesgo? ¿Cuánta carga operativa o intervención manual eliminan al automatizar estos cambios y respaldos?

### Criterio 1.4: Despliegue

- **Pipeline de entrega:** ¿Qué tan automatizado está el camino de construcción y despliegue (CI/CD)? ¿Cada cambio puede llegar a producción de forma automática o con un clic, o todavía hay pasos manuales? ¿Qué controles de calidad y seguridad están integrados en el pipeline? Como inversión en velocidad de iteración, ¿cuánto tiempo y trabajo manual por liberación les ahorra hoy esa automatización?
- **Prácticas de nube:** ¿Los componentes están contenedorizados y pueden escalar horizontalmente con facilidad? ¿La infraestructura se gestiona como código con configuraciones optimizadas, o se aprovisiona manualmente? ¿Cómo impacta esto en costos y en la capacidad de respuesta del área? ¿Cuánta carga operativa elimina gestionar la infraestructura como código frente a aprovisionar a mano?

### Criterio 1.5: Aseguramiento de Calidad

- **Calidad temprana (shift-left):** ¿Cómo se integra la calidad desde las etapas tempranas del desarrollo? ¿Siguen una estrategia de pirámide de pruebas con automatización, ambientes de prueba disponibles y uso de mocks para dependencias externas, o la calidad se valida principalmente al final del ciclo? Bajo la óptica de validar temprano: ¿cuánto antes detectan los defectos y cuánto retrabajo y costo evitan al hacerlo así en lugar de al final?

### Criterio 1.6: CFRs (Requisitos Transversales)

- **Accesibilidad:** ¿Existen lineamientos de accesibilidad definidos y qué tan consistentemente los cumplen las soluciones que desarrollan? ¿Cuánto retrabajo o riesgo de cumplimiento evita resolver accesibilidad desde el diseño en vez de remediarla después?
- **Trazabilidad y logging:** Desde una perspectiva de operación y diagnóstico, ¿qué tan estandarizados están los registros (logs) y es posible rastrear una solicitud o acción de extremo a extremo entre sistemas (p. ej. con correlation IDs)? ¿Cuánto reducen el tiempo de diagnóstico (MTTR) y el esfuerzo del equipo cuando ocurre un incidente?

---

## Subdimensión 2: DevOps

El objetivo es evaluar, desde la mirada gerencial, la madurez de la integración y el despliegue continuos, la operación en producción y la gestión de ambientes como habilitadores de la velocidad de entrega, la estabilidad y el control del negocio sobre las liberaciones.

### Criterio 2.1: Integración y Despliegue Continuo

- **Integración (build):** ¿Cómo es el flujo de integración de código en tus equipos? ¿Con qué frecuencia integran a la línea principal (a diario, cada pocos días, cada sprint), cuánto dependen de pruebas manuales para certificar la calidad, y cómo se gestiona la responsabilidad cuando un build queda en rojo? En términos de velocidad de iteración, ¿qué tan corto es el ciclo entre escribir código y tener feedback de que funciona, y cuánto tiempo manual consume hoy certificar la calidad?
- **Despliegue a producción:** ¿Con qué frecuencia despliegan a producción (varias veces al día, semanal, mensual, trimestral)? ¿Hay ventana de downtime, existen congelamientos en periodos pico, y quién decide cuándo se libera: el negocio o restricciones de TI? ¿Cuánto esfuerzo y coordinación cuesta hoy cada liberación, y cuánto valor desbloquearía poder desplegar bajo demanda?

### Criterio 2.2: Operación en Producción

- **Observabilidad:** ¿Qué capacidad tienen para detectar y diagnosticar problemas en producción (agregación de logs, trazas distribuidas, alertas, APM)? ¿Estas prácticas están estandarizadas entre equipos y probadas contra SLAs, o son ad-hoc según el equipo? Como tema de medir lo que importa: ¿qué decisiones o acciones cambian gracias a esas métricas, o se recopilan sin que muevan nada?
- **Continuidad del negocio:** Ante una caída, ¿cuál es el tiempo medio de recuperación (MTTR) que manejan habitualmente? ¿Operan en un esquema activo-pasivo o activo-activo con cero downtime? ¿Cómo se traduce esto en riesgo e impacto para el negocio? ¿Cuánta carga operativa y trabajo manual de recuperación elimina hoy la automatización de failover y respaldos?

### Criterio 2.3: Ambientes

- **Aprovisionamiento y uso:** ¿Cómo se aprovisionan los ambientes (manual vs. programático, servidores duraderos vs. efímeros, máquinas virtuales vs. contenedores/serverless)? ¿Qué tan rápido y confiable es levantar un ambiente nuevo cuando un equipo lo necesita? ¿Cuánto tiempo de espera del equipo elimina poder crear un ambiente bajo demanda frente a solicitarlo manualmente?
- **Buenas prácticas de ambientes:** ¿Cómo gestionan la configuración, los feature toggles y los secretos entre ambientes? ¿Los cambios de configuración obligan a reconstruir o redeployar la aplicación, y los secretos se manejan de forma segura y centralizada? ¿Cuánta fricción y riesgo operativo evita gestionar configuración y secretos de forma centralizada en lugar de hacerlo a mano por ambiente?

---

## Subdimensión 3: Calidad de Arquitectura

El objetivo es entender si la arquitectura actúa como habilitador de la velocidad del negocio o como fuente de dependencias y riesgo: el estilo arquitectónico, la estrategia de APIs, la vigencia del stack tecnológico, el desempeño y cómo se toman y se gobiernan las decisiones técnicas que impactan al negocio.

### Criterio 3.1: Estilo Arquitectónico

- **Estilo arquitectónico:** ¿Cómo describirías la arquitectura actual de tus sistemas: monolito muy acoplado, monolito estructurado, microservicios, orientada a eventos? ¿Existe una separación clara entre los componentes de negocio y las integraciones con terceros —incluyendo dependencias y modelo de datos—, y hay plantillas o estándares de integración reutilizables, o cada equipo lo resuelve a su manera? ¿Qué tanto habilita o frena hoy esa arquitectura la velocidad con la que pueden entregar cambios, y cuánto esfuerzo reutilizan gracias a esas plantillas?

### Criterio 3.2: Estrategia de APIs

- **Estrategia de APIs:** ¿Tienen una estrategia explícita de APIs (gateway, versionado, documentación)? ¿La documentación se mantiene sincronizada y es fácilmente descubrible para los consumidores, o los equipos tienen que revisar el código para entender cómo integrarse? ¿Esta estrategia es consistente a nivel de toda la organización o varía entre equipos? ¿Cuánto tiempo de integración y soporte entre equipos ahorra hoy poder autoservirse de las APIs frente a tener que coordinar caso por caso?

### Criterio 3.3: Stack Tecnológico

- **Stack tecnológico:** ¿Qué tan vigente y adecuado al dominio está el stack tecnológico? ¿Tienen tecnologías obsoletas, sin soporte o costosas de extender que limiten las prioridades del negocio? ¿Cómo deciden cuándo invertir en modernizar? Al priorizar esas inversiones, ¿cómo sopesan el impacto (velocidad, costo, riesgo) contra el esfuerzo de migrar?

### Criterio 3.4: Desempeño

- **Desempeño:** ¿Cómo aseguran que los sistemas cumplan con resiliencia, escalabilidad y disponibilidad? ¿Usan patrones (circuit breakers, rate limiting, caching) de forma estandarizada entre equipos, y las pruebas de rendimiento/escala están integradas al pipeline o solo se hacen antes de hitos grandes? ¿Cuánto antes detectan problemas de desempeño al validarlos de forma continua, y cuánto esfuerzo de última hora les evita?

### Criterio 3.5: Gobierno

- **Gobierno:** ¿Cómo se toman las decisiones de arquitectura: cada equipo por su cuenta, un comité central que dicta desde arriba, o un modelo donde los equipos proponen y se revisan contra estándares? ¿Cómo se registran esas decisiones y cómo se verifica su conformidad (documentación, revisiones, fitness functions integradas al build)? ¿Existe un catálogo de patrones o un foro de arquitectura que los equipos consultan antes de grandes proyectos? ¿Qué tanto ese gobierno acelera o frena la toma de decisiones, y cuánto esfuerzo manual de revisión sustituyen las validaciones automatizadas?
