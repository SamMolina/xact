# Entrevista Técnica: Jefe de Delivery — Ejemplo de entrevista

> **Tipo de documento:** Ejemplo de guion de entrevista (assessment).
>
> Este documento es un **ejemplo de entrevista** diseñado para conducir una conversación de evaluación con el **jefe de delivery** (equipos implementadores de Ecommerce y POS) y un **técnico POS** de la organización. No es un cuestionario de respuesta cerrada ni una entrevista de selección: las preguntas son **abiertas** y buscan que las personas entrevistadas describan, con ejemplos concretos, cómo opera hoy la organización en sus prácticas de ingeniería y su capacidad de despliegue. Profundiza en temas técnicos y de procesos.
>
> **Cómo usar esta guía:**
> - Recorre las subdimensiones en orden; cada una abre con su objetivo de evaluación.
> - Usa los criterios como bloques temáticos y las preguntas como disparadores de conversación.
> - Profundiza con repreguntas ("¿puedes darme un ejemplo?", "¿qué porcentaje?", "¿con qué frecuencia?", "¿cuánto tiempo les ahorra?") para obtener evidencia, no solo percepciones.
> - El objetivo es evaluar el **proceso de despliegue de soluciones a grandes comercios** y la **eficiencia en ingeniería** del equipo de delivery, entendiendo qué tan apalancadas (impacto ÷ esfuerzo) están sus prácticas técnicas.

| Nivel | Elemento | Descripción |
|-------|----------|-------------|
| 1.º | Subdimensión | Área temática que se explora durante la entrevista |
| 2.º | Criterio | Bloque de preguntas dentro de una subdimensión |
| 3.º | Pregunta | Pregunta abierta para guiar la conversación |

---

## Subdimensión 1: Prácticas de Ingeniería (Engineering Excellence)

El objetivo es evaluar la salud de las prácticas de ingeniería del equipo de delivery a lo largo del ciclo de vida —desde el análisis de requerimientos hasta el despliegue y la calidad—, entendiendo dónde se concentra el esfuerzo manual, qué prácticas dan más apalancamiento y cómo se traduce esto en velocidad y confiabilidad al implementar soluciones para grandes comercios.

### Criterio 1.1: Análisis de Requerimientos (1.6.1)

- **Análisis de Requerimientos:** Cuando llega una solicitud de un comercio para una implementación Ecommerce o POS, ¿cómo se detallan y validan los requerimientos antes de empezar a construir? ¿Qué tan consistentes y de qué calidad llegan, se capturan los requerimientos no funcionales (rendimiento, seguridad, disponibilidad), se comparan soluciones alternativas y se evalúa el valor de negocio frente al esfuerzo de la solución? ¿Cuánto retrabajo evita (o genera) hoy la forma en que analizan requerimientos?
- **Diseño de Requerimientos:** ¿Cuentan con un diseño y enfoque detallado del estado futuro, los recorridos del usuario y los flujos de proceso de una implementación? ¿Con qué frecuencia se actualizan esos artefactos y se usan realmente en las discusiones del equipo, o quedan obsoletos y se vuelven redundantes? Dame un ejemplo de cómo ese diseño les ayudó (o les faltó) a validar temprano antes de implementar en un comercio grande.

### Criterio 1.2: Arquitectura y Diseño (1.6.2)

- **Compromiso con la Arquitectura:** ¿Existe una "pista de arquitectura" (architecture runway) y CFRs definidos antes de arrancar? ¿Crean diagramas y modelos (por ejemplo C4), qué tan fácil es encontrarlos, se identifica y prioriza regularmente la deuda técnica de arquitectura, y hay documentación o sesiones suficientes para que todos entiendan el panorama, o los equipos trabajan en silos?
- **Documentación:** ¿Cómo capturan las decisiones técnicas importantes —se mantienen como ADRs, se generan especificaciones vivas a partir de pruebas bien descritas— y qué tan estandarizada y centralizada está la documentación frente a estar dispersa y desactualizada? ¿Cuánto tiempo pierde un implementador buscando o reconstruyendo conocimiento que ya existía?

### Criterio 1.3: Desarrollo (1.6.3)

- **Disciplina de Desarrollo:** Descríbeme la disciplina de desarrollo del equipo: ¿corren linting y escaneo de secretos localmente (por ejemplo vía pre-commit hooks) o solo en el pipeline?, ¿siguen prácticas de XP con un setup de fallo temprano, las pruebas se escriben de forma efectiva con el dataset correcto, identifican y atacan la deuda técnica en cada iteración haciendo refactoring, y mockean dependencias externas para no frenarse? ¿Qué tan corto es hoy el ciclo de retroalimentación al desarrollar?
- **Onboarding y Cultivación del Desarrollador:** ¿Cómo es incorporar a un nuevo integrante al equipo de delivery? ¿El onboarding está estandarizado y guiado por checklist, hay scripts automatizados para armar el entorno, cuánto tiempo toma dejarlo productivo (minutos/horas vs. un re-esfuerzo grande cada vez), y cómo transfieren conocimiento de dominio y conciencia de seguridad?
- **Prácticas de Control de Fuentes:** ¿Cómo gestionan el control de versiones? ¿Siguen desarrollo basado en trunk con feature toggles o manejan múltiples ramas con mucho esfuerzo de merge?, ¿los commits son atómicos, trazables a la tarjeta de la historia y siguen estándares de la organización en sus mensajes? ¿Cuánto esfuerzo les consume hoy integrar y portar cambios entre ramas?
- **Prácticas de Gestión de Datos:** Para las soluciones que tocan base de datos, ¿los cambios de esquema/migraciones se capturan como código y se versionan, se toman y prueban respaldos periódicamente, y el monitoreo tiene alertas habilitadas, o los cambios se hacen ad-hoc por GUI y se reacciona manualmente? Dame un ejemplo de cómo manejaron un cambio de datos en un comercio en producción.

### Criterio 1.4: Despliegue (1.6.4)

- **Pipeline:** Descríbeme el pipeline de build y despliegue. ¿Existe build automatizado (CI) y despliegue de un clic, hay monitoreo y alertas para detectar fallas de build/deploy temprano, hay escáneres de seguridad integrados, y qué tan cerca están de que cada commit pueda ir a producción?, ¿o todavía crean y despliegan artefactos manualmente? ¿Cuánto tiempo manual elimina (o sigue costando) este proceso por cada despliegue a un comercio?
- **Prácticas de Nube:** ¿Cómo están construidos y operados los componentes? ¿Están contenedorizados y desacoplados, escalan horizontalmente con facilidad, y la infraestructura se gestiona como código (IaC) con configuraciones y políticas óptimas (escalado, logs), o se crea manualmente una vez y nunca se corrige? ¿Qué tanto les permite esto absorber picos de carga de grandes comercios sin intervención manual?

### Criterio 1.5: Aseguramiento de la Calidad (1.6.5)

- **Pruebas/Calidad Shift-Left:** ¿Cómo aplican la pirámide de pruebas en las implementaciones? ¿Cubren todas las capas con pruebas efectivas y el dataset correcto, disponen de un entorno de pruebas, qué tan automatizado está, y usan mocks en los entornos bajos para cubrir todos los escenarios que dependen de servicios externos (pasarelas de pago, integraciones POS/Ecommerce)? ¿En qué momento del ciclo se detectan hoy la mayoría de los defectos?

### Criterio 1.6: CFRs (1.6.6)

- **Accesibilidad:** ¿Existen lineamientos de accesibilidad y qué tan consistentemente los sigue el equipo en las soluciones que entregan? ¿Todas las soluciones desarrolladas cumplen los requisitos de accesibilidad definidos, solo algunas en cierta medida, o no se considera el aspecto?
- **Logging:** ¿Qué tan estandarizados están los niveles y patrones de log? ¿Pueden trazar una solicitud o acción de extremo a extremo a través de los sistemas usando identificadores de correlación, solo parcialmente, o los logs se usan de forma aleatoria y la trazabilidad es prácticamente imposible? Dame un ejemplo de cuánto tardan en diagnosticar un incidente en un comercio con el nivel de logging actual.

---

## Subdimensión 2: DevOps (1.2)

El objetivo es evaluar la capacidad de integración, despliegue y operación en producción del equipo de delivery: con qué frecuencia, fricción y riesgo ponen soluciones en manos de grandes comercios, y qué tan apalancadas están sus prácticas de CI/CD, observabilidad y entornos.

### Criterio 2.1: Integración y Despliegue Continuo (1.2.1)

- **Build (Integración Continua):** Descríbeme cómo integra el equipo su código: ¿los cambios viven en ramas privadas de larga duración que se integran cada varias semanas, o la integración es verdaderamente continua sobre la mainline?, ¿el proceso de build incluye una buena mezcla de pruebas (unitarias, de integración, de contrato, funcionales) en verde, cuánta prueba manual se necesita aún para certificar calidad, y qué pasa cuando el build queda en rojo (quién lo toma, cuánto tarda en arreglarse)?
- **Despliegue:** Para una solución a un gran comercio, ¿con qué frecuencia despliegan a producción (mensual o menos, semanal, casi diario, varias veces al día bajo demanda)?, ¿el despliegue es manual o automatizado, hay ventana de downtime o es cero downtime (blue-green, rolling, canary), y quién decide cuándo se libera —el negocio o restricciones de TI? ¿Existen congelamientos preventivos en periodos pico (Navidad, Black Friday) y qué tan negociables son?
- **(Contexto a profundizar:** este es el corazón del objetivo de "proceso de despliegue a grandes comercios": ata las respuestas al tiempo de ciclo, al riesgo de fallas que impacten al comercio y al esfuerzo manual que se podría eliminar.)*

### Criterio 2.2: Operaciones de Producción (1.2.2)

- **Observabilidad:** ¿Qué patrones de observabilidad usan (agregación de logs, trazas distribuidas, health checks, alertas, APM) y qué tan maduros están: ausentes, esporádicos por equipo, documentados con implementaciones variadas, estandarizados, o probados para cumplir SLAs? ¿Detectan un problema en un comercio antes de que el comercio o el usuario lo note, o se enteran por el cliente? ¿Qué decisiones cambian con la data que observan?
- **Continuidad del Negocio:** Si cae un servicio que atiende a un comercio, ¿cuál es el tiempo medio de recuperación (MTTR) hoy —24 horas o más, entre 12 y 24, entre 6 y 12, de 2 a 6 horas— y operan en esquema activo-pasivo o activo-activo con cero downtime? Cuéntame el último incidente real y cuánto tardaron en restablecer el servicio.

### Criterio 2.3: Entornos (1.2.3)

- **Aprovisionamiento y uso:** ¿Cómo se aprovisionan los entornos donde corren las soluciones? ¿Son servidores bare metal o máquinas virtuales provisionadas manualmente y de larga duración, máquinas virtuales aprovisionadas programáticamente, o contenedores/funciones serverless efímeros e inmutables aprovisionados programáticamente? ¿Cuánto tiempo y trabajo manual les cuesta levantar o replicar un entorno para un nuevo comercio?
- **Buenas Prácticas (configuración, toggles y secretos):** ¿Cómo gestionan la configuración por entorno (embebida en el artefacto y requiere rebuild, o externalizada y trazable a un check-in), los feature toggles (embebidos vs. externalizados a nivel de feature de negocio) y los secretos (embebidos/manuales vs. en un servidor de gestión de secretos cifrado)? ¿Cuánto les permite esto desplegar a distintos comercios sin reconstruir ni intervenir manualmente?

---

## Cierre: Mapeo de dolores

> Bloque de síntesis (no puntuado). Úsalo al final para consolidar y priorizar los dolores detectados a lo largo de la entrevista.

- **Principales dolores:** De todo lo que conversamos —prácticas de ingeniería (requerimientos, arquitectura, desarrollo, despliegue, calidad, CFRs) y DevOps (integración y despliegue continuo, operaciones en producción y entornos)—, ¿cuáles son los **3 dolores** que más les frenan hoy al entregar e implementar soluciones a grandes comercios? Para cada uno, ¿qué impacto tiene (tiempo perdido, defectos, retrabajo, riesgo para el comercio) y qué tan grande sería el apalancamiento de resolverlo frente al esfuerzo que implica?
