# Entrevista Jefe de Desarrollo — Ejemplo de entrevista

> **Tipo de documento:** Ejemplo de guion de entrevista (assessment).
>
> Este documento es un **ejemplo de entrevista** diseñado para conducir una conversación de evaluación con un **Jefe de Desarrollo** y/o un **líder técnico** de un equipo. No es un cuestionario de respuesta cerrada: las preguntas son **abiertas** y, dado el perfil técnico del entrevistado, buscan **profundizar en el detalle de implementación** —cómo se trabaja realmente (way of working), cómo fluye el ciclo de vida del software (SDLC), qué lineamientos técnicos rigen y qué tan flexibles son, el tech stack, la entrega y el runtime de despliegue, la eficiencia en ingeniería, la estrategia de pruebas y el monitoreo de sistemas— para terminar **mapeando los dolores** del equipo.
>
> **Cómo usar esta guía:**
> - Recorre las subdimensiones en orden; cada una abre con su objetivo de evaluación.
> - Usa los criterios como bloques temáticos y las preguntas como disparadores de conversación.
> - Profundiza con repreguntas técnicas ("¿puedes mostrarme un ejemplo concreto?", "¿qué herramienta/versión?", "¿qué porcentaje?", "¿con qué frecuencia?", "¿quién lo decide?", "¿qué pasa cuando falla?", "¿cuánto tiempo les ahorra?", "¿qué trabajo manual eliminó?") para obtener evidencia, no solo percepciones.
> - Las preguntas están planteadas bajo la óptica de **ingeniería efectiva** ("The Effective Engineer", Edmond Lau): efectividad = **impacto ÷ tiempo (apalancamiento)**. No basta con saber si una práctica o herramienta existe; interesa cuánto apalancamiento genera —velocidad de iteración, aprendizaje, priorización del trabajo de alto impacto, métricas que guían decisiones y reducción de carga operativa.
> - El objetivo es entender el way of working y el SDLC del equipo, los lineamientos técnicos y su flexibilidad, mapear el tech stack, comprender la entrega continua (continuous delivery) y el runtime de despliegue (deployment runtime), evaluar la eficiencia en ingeniería, la estrategia de pruebas y el monitoreo de sistemas, y **mapear los principales dolores** que frenan al equipo.

| Nivel | Elemento | Descripción |
|-------|----------|-------------|
| 1.º | Subdimensión | Área temática que se explora durante la entrevista |
| 2.º | Criterio | Bloque de preguntas dentro de una subdimensión |
| 3.º | Pregunta | Pregunta abierta para guiar la conversación |

---

## Subdimensión 1: Excelencia en Ingeniería (Prácticas de Ingeniería)

El objetivo es entender en detalle el **way of working** y el **SDLC** del equipo —desde el análisis de requisitos hasta el despliegue y la calidad—, qué prácticas de ingeniería son estándar, qué tan automatizadas están y cuánto apalancan la velocidad de iteración y la entrega de valor. Aprovecha esta subdimensión para empezar a **mapear los dolores** técnicos del día a día.

### Criterio 1.1: Análisis y Diseño de Requisitos

- **Análisis de requisitos:** ¿Cómo llega el trabajo al equipo y qué tan completos están los requisitos cuando los reciben? Cuéntame en concreto si se capturan los requisitos no funcionales (seguridad, rendimiento, accesibilidad), si se comparan soluciones alternativas y si se evalúa el valor de negocio antes de empezar a construir. Desde el apalancamiento: ¿cuánto retrabajo o desperdicio les evita (o les genera hoy) la calidad de los requisitos al inicio? Dame un ejemplo reciente donde un requisito mal definido los hizo rehacer trabajo.
- **Diseño de requisitos:** Antes de codificar, ¿existen diseños del estado futuro, recorridos de usuario y flujos de proceso? ¿Quién los produce, dónde viven y qué tan actualizados se mantienen, o tienden a quedar obsoletos? ¿Qué tanto les permiten validar ideas temprano y acelerar la iteración, en lugar de ser documentación que nadie consulta?

### Criterio 1.2: Arquitectura y Documentación

- **Involucramiento de arquitectura:** ¿Cómo se materializa la arquitectura como insumo del equipo? ¿Tienen diagramas y modelos (p. ej. C4) accesibles y vigentes, identifican y priorizan deuda técnica de arquitectura de forma regular, y hay sesiones/documentación para entender el panorama completo, o trabajan en silos? Técnicamente, ¿cómo deciden qué deuda atacar primero según su impacto en la velocidad frente al esfuerzo de resolverla?
- **Documentación:** ¿Cómo capturan y conservan las decisiones técnicas importantes (p. ej. ADRs)? ¿La documentación funcional se genera a mano o se deriva de los tests (live specifications), y está estandarizada y centralizada o dispersa y desactualizada? ¿Cuánto tiempo de búsqueda, retrabajo o decisiones repetidas les ahorra hoy esa documentación?

### Criterio 1.3: Disciplina de Desarrollo y Personas

- **Disciplina de desarrollo:** Descríbeme el way of working diario: ¿qué prácticas de XP siguen (TDD, pair/mob, revisiones de código), qué corre en local antes de subir cambios (linting, escaneo de secretos, pruebas vía pre-commit hooks) versus en el pipeline? ¿Las pruebas son efectivas (dataset correcto) o solo dan sensación de cobertura? ¿La deuda técnica se atiende en cada iteración y refactorizan como parte normal del trabajo, o se posterga? ¿Cuánto acortan estas prácticas el ciclo de feedback y cuántos defectos en producción evitan?
- **Onboarding y desarrollo de personas:** Cuando entra un nuevo desarrollador, ¿el setup está estandarizado y automatizado por scripts (minutos/horas) o cada quien arma su entorno (días de reproceso)? ¿Cómo transmiten el conocimiento del dominio y la conciencia de seguridad? Como inversión de largo plazo, ¿cuánto tiempo del equipo libera un onboarding ágil frente a acompañar a cada persona a mano?
- **Control de versiones:** ¿Cómo trabajan con el código (estrategia de ramas, trunk-based vs. ramas largas, feature toggles, atomicidad y trazabilidad de los commits hacia las historias)? ¿Cuánta fricción o reprocesos de integración genera hoy ese flujo? ¿Cuánto tiempo pierden resolviendo conflictos o integraciones tardías que un flujo más estandarizado eliminaría?
- **Gestión de datos:** ¿Cómo manejan los cambios a bases de datos (migraciones versionadas como código, respaldos tomados y probados periódicamente, monitoreo y alertas)? ¿Qué tan automatizado está esto o se hace por la GUI a mano? ¿Cuánta carga operativa y riesgo elimina (o les añade hoy) la forma en que gestionan esos cambios y respaldos?

### Criterio 1.4: Despliegue y Prácticas de Nube

- **Pipeline de entrega:** Llévame por el pipeline real de build y despliegue: ¿es CI/CD completo donde cada commit puede ir a producción, despliegue de un clic con commits seleccionados, o todavía hay pasos manuales? ¿Qué controles de calidad y seguridad (escáneres, monitoreo/alertas de fallos de build/deploy) están integrados? Como inversión en velocidad de iteración, ¿cuánto tiempo y trabajo manual por liberación les ahorra hoy esa automatización?
- **Prácticas de nube:** ¿Los componentes están contenedorizados y escalan horizontalmente con facilidad, o están acoplados? ¿La infraestructura es código (IaC) con configuraciones y políticas optimizadas (escalado, logs), o se aprovisiona a mano una vez y nunca se corrige? ¿Cuánta carga operativa y cuánto sobre/sub-aprovisionamiento de recursos elimina (o les cuesta hoy) la forma en que gestionan la infraestructura?

### Criterio 1.5: Aseguramiento de Calidad (Shift-Left)

- **Calidad temprana (shift-left):** ¿Cómo integran la calidad desde etapas tempranas? ¿Siguen la pirámide de pruebas con todas sus capas, escriben pruebas efectivas con el dataset correcto en cada capa, tienen ambiente de prueba disponible, automatización y mocks para dependencias externas, o la calidad se valida principalmente al final? Bajo la óptica de validar temprano: ¿cuánto antes detectan los defectos y cuánto retrabajo y costo evitan al hacerlo así?

### Criterio 1.6: Requisitos Transversales (CFRs)

- **Accesibilidad:** ¿Existen lineamientos de accesibilidad definidos y qué tan consistentemente los cumplen las soluciones que desarrollan? ¿Cuánto retrabajo o riesgo de cumplimiento evita resolver accesibilidad desde el diseño en vez de remediarla después?
- **Trazabilidad y logging:** ¿Qué tan estandarizados están los niveles y patrones de log, y pueden rastrear una solicitud o acción de extremo a extremo entre sistemas (p. ej. con correlation IDs)? ¿Cuánto reduce el tiempo de diagnóstico (MTTR) y el esfuerzo del equipo cuando ocurre un incidente?

---

## Subdimensión 2: DevOps

El objetivo es evaluar a fondo la **entrega continua (continuous delivery)** y el **runtime de despliegue (deployment runtime)**, la operación en producción y el **monitoreo de sistemas**, y la gestión de ambientes, como habilitadores de la velocidad, la estabilidad y el control del negocio sobre las liberaciones. Continúa **mapeando dolores** operativos.

### Criterio 2.1: Integración y Despliegue Continuo

- **Integración (build):** Descríbeme el flujo de integración: ¿dónde ocurren los check-ins (mainline, ramas cortas, ramas largas), con qué frecuencia integran (a diario, cada pocos días, cada sprint), qué mezcla de pruebas corre el build (unitarias, integración, contrato, funcionales, aceptación) y qué tan verdes y rápidas son? ¿Cuánto dependen aún de pruebas manuales para certificar calidad y cómo se gestiona la responsabilidad cuando un build queda en rojo? En velocidad de iteración: ¿qué tan corto es el ciclo entre escribir código y tener feedback de que funciona?
- **Despliegue a producción (deployment runtime):** ¿Cuál es el artefacto y la estrategia de despliegue (EAR/WAR en contenedor compartido, VM inmutable, contenedores con rolling/canary/blue-green, grupos de contenedores tipo helm)? ¿Con qué frecuencia despliegan, hay ventana de downtime, existen congelamientos en periodos pico y quién decide cuándo se libera: el negocio o restricciones de TI? ¿Cuánto esfuerzo y coordinación cuesta hoy cada liberación y cuánto valor desbloquearía desplegar bajo demanda varias veces al día?

### Criterio 2.2: Operación en Producción

- **Observabilidad (monitoreo de sistemas):** ¿Qué stack de observabilidad usan (agregación de logs, trazas distribuidas, health checks, alertas, APM)? ¿Estas prácticas son ad-hoc por equipo, están documentadas, estandarizadas o probadas contra SLAs? Como tema de medir lo que importa: ¿qué decisiones o acciones cambian gracias a esas métricas y alertas, o se recopilan sin que muevan nada? Dame un ejemplo de un incidente que detectaron (o se les escapó) por el monitoreo.
- **Continuidad del negocio:** Ante una caída, ¿cuál es el MTTR habitual y operan en activo-pasivo o activo-activo con cero downtime? ¿Cómo se traduce eso en riesgo e impacto? ¿Cuánta carga operativa y trabajo manual de recuperación elimina hoy la automatización de failover y respaldos?

### Criterio 2.3: Ambientes

- **Aprovisionamiento y uso:** ¿Cómo se aprovisionan los ambientes (manual vs. programático; bare metal, VMs duraderas, VMs efímeras inmutables, contenedores/serverless)? ¿Qué tan rápido y confiable es levantar un ambiente nuevo cuando el equipo lo necesita? ¿Cuánto tiempo de espera del equipo elimina poder crear un ambiente bajo demanda frente a solicitarlo a mano?
- **Buenas prácticas de ambientes:** ¿Cómo gestionan configuración, feature toggles y secretos entre ambientes? ¿Un cambio de configuración obliga a reconstruir/redeployar, los toggles requieren conocer internals de la app, y los secretos están en un secrets manager o embebidos/manuales? ¿Cuánta fricción y riesgo operativo evita gestionar configuración y secretos de forma centralizada y trazable en lugar de hacerlo a mano por ambiente?

---

## Subdimensión 3: Calidad de Arquitectura

El objetivo es entender, con profundidad técnica, si la arquitectura habilita o frena la velocidad del equipo, **mapear el tech stack**, y comprender qué **lineamientos técnicos** rigen las decisiones y qué tan flexibles son. Cierra esta subdimensión consolidando los **dolores** arquitectónicos.

### Criterio 3.1: Estilo Arquitectónico

- **Estilo arquitectónico:** ¿Cómo describirías técnicamente la arquitectura actual (monolito muy acoplado, monolito estructurado, microservicios orientados a servicios, microservicios orientados a eventos, serverless)? ¿Hay una separación limpia entre la lógica de negocio y las integraciones con terceros, y existen plantillas o estándares de integración reutilizables que aíslen esa lógica y las expectativas de resiliencia, o cada equipo lo resuelve a su manera? ¿Qué tanto habilita o frena hoy esa arquitectura la velocidad con la que entregan cambios, y cuánto esfuerzo reutilizan gracias a esas plantillas?

### Criterio 3.2: Estrategia de APIs

- **Estrategia de APIs:** ¿Cómo manejan las APIs técnicamente (uso de API gateway y para qué —proxy, zero-downtime, auth, rate limiting, circuit breaker—, estrategia de versionado por URL o header, y documentación)? ¿La documentación se mantiene sincronizada con la implementación (p. ej. generada desde tests y publicada en un portal) o los consumidores tienen que leer el código para integrarse? ¿Cuánto tiempo de integración y soporte entre equipos ahorra hoy poder autoservirse de las APIs frente a coordinar caso por caso?

### Criterio 3.3: Stack Tecnológico

- **Stack tecnológico:** Mapéame el tech stack actual (lenguajes, frameworks, data stores, plataforma) y qué tan vigente y adecuado al dominio está: ¿tienen tecnologías obsoletas, sin soporte, con licencias costosas o force-fitted al dominio que limiten las prioridades del negocio? ¿Cómo deciden cuándo invertir en modernizar y qué tan flexible es cambiar de tecnología? Al priorizar esas inversiones, ¿cómo sopesan el impacto (velocidad, costo, riesgo) contra el esfuerzo de migrar?

### Criterio 3.4: Desempeño

- **Desempeño, resiliencia y escalabilidad:** ¿Cómo aseguran resiliencia, escalabilidad y disponibilidad? ¿Usan patrones (circuit breakers, timeouts, service discovery, rate limiting, throttling, caching) de forma estandarizada entre equipos y probados contra SLAs, y las pruebas de rendimiento/escala están automatizadas en el pipeline o solo se corren antes de hitos grandes? ¿Cuánto antes detectan problemas de desempeño al validarlos de forma continua, y cuánto esfuerzo de última hora les evita?

### Criterio 3.5: Gobierno

- **Gobierno y lineamientos técnicos:** ¿Cómo se toman las decisiones de arquitectura: cada equipo por su cuenta, un comité central que dicta desde arriba, o un modelo donde los equipos proponen y se revisan contra estándares? ¿Qué tan flexibles son esos lineamientos y cómo se registran y hacen cumplir (documentación, revisiones, observaciones de análisis estático, fitness functions integradas al build, catálogo de patrones)? ¿Qué tanto ese gobierno acelera o frena la toma de decisiones, y cuánto esfuerzo manual de revisión sustituyen las validaciones automatizadas?

---

## Cierre: Mapeo de dolores

> Bloque de síntesis (no puntuado). Úsalo al final para consolidar y priorizar los dolores detectados a lo largo de la entrevista.

- **Principales dolores:** De todo lo que conversamos —way of working/SDLC, entrega y despliegue, monitoreo, tech stack, arquitectura y lineamientos—, ¿cuáles son los **3 dolores** que más les frenan hoy? Para cada uno, ¿qué impacto tiene (tiempo perdido, defectos, retrabajo, riesgo) y qué tan grande sería el apalancamiento de resolverlo frente al esfuerzo que implica?
