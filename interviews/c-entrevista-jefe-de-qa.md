# Tech-QA: Jefe de QA — Ejemplo de entrevista

> **Tipo de documento:** Ejemplo de guion de entrevista (assessment).
>
> Este documento es un **ejemplo de entrevista** para conducir una conversación de evaluación técnica con el **Jefe de QA** y un **tester senior** de la organización. No es un cuestionario de respuesta cerrada ni una entrevista de contratación: las preguntas son **abiertas** y buscan que las personas entrevistadas describan, con ejemplos concretos, cómo opera hoy el aseguramiento de la calidad. Dado el perfil técnico de los entrevistados, profundiza en el detalle de prácticas, herramientas y métricas.
>
> **Cómo usar esta guía:**
> - Recorre las subdimensiones en orden; cada una abre con su objetivo de evaluación.
> - Usa los criterios como bloques temáticos y las preguntas como disparadores de conversación.
> - Profundiza con repreguntas ("¿puedes darme un ejemplo?", "¿qué porcentaje?", "¿con qué frecuencia?") para obtener evidencia, no solo percepciones.
> - El objetivo es entender y **mapear la estrategia de calidad**, su forma de trabajo (WoW), herramientas y métricas, y valorar el aseguramiento de la calidad como una palanca de **eficiencia en ingeniería** (mayor impacto por unidad de tiempo invertido).

| Nivel | Elemento | Descripción |
|-------|----------|-------------|
| 1.º | Subdimensión | Área temática que se explora durante la entrevista |
| 2.º | Criterio | Bloque de preguntas dentro de una subdimensión |
| 3.º | Pregunta | Pregunta abierta para guiar la conversación |

---

## Subdimensión 1: Aseguramiento de la calidad

El objetivo de esta subdimensión es mapear la estrategia de calidad de extremo a extremo: la mentalidad de calidad incorporada en el equipo, la solidez de la estrategia de pruebas, la organización y el gobierno del testing (procesos, métricas, herramientas) y la madurez de la pirámide de pruebas. Buscamos entender qué tan bien el aseguramiento de la calidad acelera la entrega (iteración rápida, retroalimentación temprana, menor carga operativa) en lugar de actuar como un cuello de botella manual al final del ciclo.

### Criterio 1.1: Mentalidad de Calidad Incorporada

- **Comprensión de los Objetivos de Negocio:** ¿Qué tanto conoce el equipo de QA el negocio y el producto que prueba? Cuéntenme cómo entienden las áreas funcionales, su alineación con la visión de producto, los requisitos no funcionales (seguridad, accesibilidad, desempeño) y los distintos tipos de usuarios. ¿Tienen acceso directo a los stakeholders de producto y llegan a dar feedback sobre las funcionalidades, o prueban "a ciegas" sobre áreas aisladas? ¿Cómo influye ese entendimiento en priorizar las pruebas de mayor impacto?
- **Comprensión Técnica del Proyecto:** ¿Qué nivel de conocimiento técnico y de arquitectura tiene el equipo de QA sobre el producto/plataforma? Descríbanme con un ejemplo cómo usan ese conocimiento: ¿solo conocen el stack, o entienden la arquitectura lo suficiente para dirigir las pruebas hacia las fortalezas/debilidades conocidas y dar feedback para mejorar u optimizar el diseño? ¿Cuánto les ayuda esto a encontrar antes los defectos de mayor riesgo?

### Criterio 1.2: Estrategia de Pruebas

- **Preparación de las Pruebas:** ¿Existe una estrategia de pruebas documentada y, sobre todo, viva? Cuéntenme qué tan actualizada está, con qué frecuencia se revisa con base en el feedback de implementación, qué tan compartida está entre los miembros del equipo (¿fragmentada o entendida por todos?) y si el equipo de desarrollo completo contribuye a ella. ¿Qué tan seguido la ejecución real se desvía de lo que dice la estrategia?
- **Estándares por Defecto (Sensible Defaults):** ¿Tienen definidos "sensible defaults" o estándares mínimos de calidad por defecto (criterios de aceptación, definition of done de pruebas, convenciones)? Descríbanme cuáles son, qué tan consistentemente se siguen, cómo se mantienen al día frente a cambios del producto y la tecnología, y si reflejan prácticas pioneras o de referencia de la industria. ¿Cuánto reducen la fricción y las decisiones repetitivas del día a día?

### Criterio 1.3: Organización del Testing

- **Proceso de Pruebas:** Descríbanme el proceso de testing que sigue una historia o épica de principio a fin. ¿Está definido y documentado, qué tan consistentemente lo sigue el equipo a lo largo de las historias, y qué tan empoderado está el equipo para ajustar o tomar decisiones sobre las expectativas del proceso cuando hace falta? ¿Dónde se rompe o se vuelve inconsistente el flujo?
- **Métricas:** ¿Qué métricas de calidad y de testing miden hoy y cómo las usan? Cuéntenme cuáles son, con qué frecuencia las revisan y si reflejan de verdad la calidad del software y de las pruebas o son métricas de actividad que pueden volverse disfuncionales. ¿Siguen tendencias en el tiempo y qué decisiones concretas han cambiado a partir de esos datos, o las métricas son más bien un "afterthought"?
- **Gestión de Pruebas:** ¿Usan alguna herramienta o práctica de gestión de pruebas (test management)? Descríbanme qué tan consistentemente la usa el equipo, qué tan al día están los casos, la automatización y la documentación, y qué tan fácil es trazar resultados de ejecuciones anteriores. ¿Hay gaps entre lo que está en la herramienta y lo que realmente se ejecuta? ¿Cuánto tiempo les ahorra (o les cuesta) mantenerla?

### Criterio 1.4: Pirámide de Pruebas

- **Pruebas Unitarias:** ¿Cómo es la práctica de pruebas unitarias y dev box testing en el equipo? Cuéntenme si es regular y consistente, si tienen herramientas de cobertura de código en uso (y si la cobertura se mira y se mejora activamente), si los unit tests pasan por code review, y si la estrategia de automatización se diseña a partir de la cobertura unitaria. ¿QA da feedback a desarrollo sobre las pruebas unitarias y el equipo respeta colectivamente la pirámide de pruebas?
- **Pruebas Funcionales:** Descríbanme cómo hacen las pruebas funcionales y de regresión. ¿Qué porcentaje es manual vs. automatizado, qué tan bien documentados y mapeados están los casos a la funcionalidad actual, y con qué frecuencia escapan defectos a producción? ¿Los tests de regresión se actualizan junto con (o antes de) que se desarrolle la funcionalidad, qué tan confiable es la suite automatizada y cuánto tiempo de calidad pueden dedicar a pruebas exploratorias y de NFR?
- **Automatización:** ¿Cuál es el estado de la automatización de pruebas y su integración con CI? Cuéntenme qué tan exhaustiva y robusta es la cobertura automatizada de la regresión, si los tests corren en cada build y el equipo confía en sus resultados para verificar el build, qué tan optimizados están los tiempos de build, y si analizan y corrigen cada fallo de forma oportuna. ¿Tienen también automatizadas las verificaciones de seguridad y las pruebas de desempeño? ¿Cuánto trabajo manual de regresión les ha eliminado la automatización?

---

## Cierre: Mapeo de dolores

> Bloque de síntesis (no puntuado). Úsalo al final para consolidar y priorizar los dolores detectados a lo largo de la entrevista.

- **Principales dolores:** De todo lo que conversamos —mentalidad de calidad y comprensión del negocio/arquitectura, estrategia de pruebas, organización del testing (proceso, métricas y herramientas de gestión) y la pirámide de pruebas (unitarias, funcionales y automatización)—, ¿cuáles son los **3 dolores** que más les frenan hoy? Para cada uno, ¿qué impacto tiene (tiempo perdido, defectos que escapan a producción, retrabajo, riesgo) y qué tan grande sería el apalancamiento de resolverlo frente al esfuerzo que implica?
