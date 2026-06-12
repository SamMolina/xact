# Tecnología y herramientas — Ejemplo de entrevista

> **Tipo de documento:** Ejemplo de guion de entrevista (assessment).
>
> Este documento es un **ejemplo de entrevista** diseñado para conducir una conversación de evaluación con líderes de tecnología, ingeniería y producto. No es un cuestionario de respuesta cerrada: las preguntas son **abiertas** y buscan que la persona entrevistada describa, con ejemplos concretos, cómo opera hoy la organización.
>
> **Cómo usar esta guía:**
> - Recorre las subdimensiones en orden; cada una abre con su objetivo de evaluación.
> - Usa los criterios como bloques temáticos y las preguntas como disparadores de conversación.
> - Profundiza con repreguntas ("¿puedes darme un ejemplo?", "¿qué porcentaje?", "¿con qué frecuencia?") para obtener evidencia, no solo percepciones.
> - El objetivo es valorar la salud técnica de la organización, su arquitectura y su ecosistema de herramientas como habilitadores de la velocidad del negocio.

| Nivel | Elemento | Descripción |
|-------|----------|-------------|
| 1.º | Subdimensión | Área temática que se explora durante la entrevista |
| 2.º | Criterio | Bloque de preguntas dentro de una subdimensión |
| 3.º | Pregunta | Pregunta abierta para guiar la conversación |

---

## Subdimensión 1: Gestión de Implementación, Lanzamiento y Observabilidad

El objetivo aquí es evaluar la salud de la tubería técnica (CI/CD) y la capacidad real de la organización para poner valor en manos del usuario con alta frecuencia, baja fricción y bajo riesgo regulatorio.

### Criterio 1.1: Automatización, Resiliencia y Entrega Continua

- **Flujo a Producción:** Descríbeme el viaje que realiza una línea de código desde que el desarrollador la termina hasta que llega a producción. ¿Qué porcentaje de este proceso (pruebas de integración, regresión, validaciones de seguridad) está automatizado y cuántos pasos o aprobaciones manuales se requieren todavía?
- **Frecuencia y Tiempos (Lead Time):** En la práctica, ¿con qué frecuencia realizan despliegues a producción (ej. varias veces al día, una vez al mes, una vez al trimestre)? ¿El plazo promedio para que un cambio menor llegue a producción es inferior a un mes?
- **Entornos y Simulación:** ¿Los equipos cuentan con entornos no productivos (Staging, Sandbox) idénticos a producción para simular transacciones de pago, integraciones con marcas (Visa, Mastercard) o pruebas de estrés de forma efectiva y segura?

### Criterio 1.2: Métricas de Ingeniería, Estabilidad y Experimentación

- **Indicadores de Desempeño Técnico:** ¿Miden actualmente métricas clave de entrega de software como las DORA metrics (frecuencia de despliegue, tiempo de ciclo, tasa de fallos en cambios, tiempo medio de recuperación)? Si es así, ¿cómo usan esta data para mejorar el proceso?
- **Calidad tras el Lanzamiento:** Una vez que se libera una nueva funcionalidad de pago, ¿qué tan común es que se presenten incidentes graves de Prioridad 1 o 2 (caídas de plataforma, rechazos masivos de transacciones)? ¿Cuentan con la infraestructura de observabilidad necesaria (logs, trazas distribuidas, métricas en tiempo real) para detectar y solucionar problemas antes de que el comercio o el usuario lo note?
- **Cultura y Herramientas de Experimentación:** Si el equipo de producto quiere realizar un experimento en vivo (pruebas A/B o despliegues progresivos mediante Feature Flags), ¿disponen de la infraestructura técnica para segmentar usuarios y capturar data de uso proactivamente, o es un proceso técnicamente inviable hoy en día?

---

## Subdimensión 2: Arquitectura y Topología de Equipos

Esta dimensión busca entender si la arquitectura de software actúa como un habilitador de la velocidad del negocio o si genera dependencias masivas que congelan el roadmap.

### Criterio 2.1: Modularidad, Dominios y Acoplamiento

- **Alineación Arquitectura-Negocio:** ¿Cómo está estructurada la arquitectura del core y los canales de pago? ¿Es modular y está alineada a dominios y capacidades claras del negocio (ej. microservicios separados para adquirencia, procesamiento, disputas), o es un monolito altamente acoplado?
- **Independencia de los Equipos:** Si un squad de producto necesita modificar su software o lanzar una mejora en su flujo de pago, ¿puede hacerlo de forma autónoma e independiente, o requiere coordinar y alinearse regularmente con otros 3 o 4 equipos debido al riesgo de romper el sistema de alguien más? ¿Utilizan estrategias como pruebas de contrato (contract testing) para mitigar este riesgo?
- **Responsabilidad de la Arquitectura:** ¿Quién es el dueño final de la arquitectura del producto? ¿Los equipos de producto tienen la responsabilidad y autonomía para evolucionar la arquitectura de sus propios componentes (arquitectura evolutiva), o dependen de un comité centralizado de arquitectura que dicta las reglas desde arriba?

### Criterio 2.2: Capacidades de Plataforma y Requisitos No Funcionales (NFRs)

- **Ingeniería de Plataforma:** ¿Qué capacidades técnicas de base provee la organización para acelerar el desarrollo (ej. infraestructura como código -IaC-, automatización en la nube, pruebas de seguridad integradas en el pipeline)? ¿Existe el concepto de un "Equipo de Plataforma" que cree herramientas para facilitarle la vida a los equipos de producto?
- **Requisitos No Funcionales:** En una industria tan regulada como payments (PCI-DSS, alta disponibilidad, tokenización), ¿cómo aseguran que los equipos de producto comprendan e incorporen orgánicamente los requisitos de seguridad y escalabilidad desde las fases tempranas del desarrollo, en lugar de verlos como una auditoría de último minuto?
- **Visión Única:** ¿Existe un mapa o una visión unificada de la arquitectura que conecte y sustente la experiencia completa del cliente a través de todos los canales y productos?

---

## Subdimensión 3: Ecosistema de Herramientas y Marcos de Trabajo

El propósito de este último bloque es evaluar la fricción operativa del día a día de los equipos provocada por su stack de herramientas y el nivel de gobierno sobre el mismo.

### Criterio 3.1: Cobertura del Ciclo de Vida y Fragmentación

- **Herramientas de Estrategia y Operación:** Si revisamos el ciclo de vida completo del producto, ¿con qué herramientas cuentan hoy para gestionar cada etapa?
  - **Estrategia y Roadmaps:** ¿Tienen un lugar centralizado para visibilizar la estrategia, métricas y el roadmap de producto (ej. Jira Product Discovery, Productboard)?
  - **Delivery y Backlog:** ¿Cómo registran el backlog y miden el avance diario (ej. Jira, Azure DevOps)?
  - **Colaboración y Conocimiento:** ¿Dónde se documenta el conocimiento y los procesos (ej. Confluence, Miro, Notion)?
  - **Diseño:** ¿Cuentan con un Sistema de Diseño (Design System) compartido y actualizado en herramientas como Figma para agilizar la consistencia visual?
- **Integración del Stack:** ¿Qué tan bien conversan estas herramientas entre sí? ¿La información fluye de manera nativa (mínimas superposiciones) o los equipos pasan demasiado tiempo duplicando datos manualmente de una plataforma a otra para reportar a los distintos stakeholders?
