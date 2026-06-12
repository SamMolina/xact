---
name: create-interview
description: >-
  Generates an X-Act technical-assessment interview guide from a title, one or
  more pillars, and an interview goal. The interview assesses an organization's
  technical maturity by talking to its technology/engineering leaders — it is
  NOT a candidate or job interview. Use when the user asks to create an
  assessment interview, build an interview guide, draft assessment questions,
  or generate an interview for given X-Act pillars. Maps each ingressed pillar
  to an X-Act node (category or module), and each node to an interview
  sub-dimension.
---

# Create Interview (X-Act)

Generates an interview guide (open-ended assessment script) for the X-Act framework. The interview is a **technical assessment of an organization**: the interviewees are its technology, engineering, and product leaders, and their answers place the organization on the X-Act maturity scale. It is **not** a candidate/job interview — never generate hiring or screening questions.

## Inputs (ask if missing)

1. **Title** — name of the interview (e.g. "Tecnología y herramientas").
2. **Pillars** — one or more areas to assess (the user's business-facing terms). Accept a list. Resolve **each** pillar to one X-Act node — a **category** (`N`) or a **module** (`N.x`) — see [Pillars → Nodes mapping](#pillars--nodes-mapping). The resolved node defines the sub-dimension's scope, and **each pillar becomes its own sub-dimension** in the interview.
3. **Goal** — what the interview aims to evaluate / the business question behind it.

If any input is missing, ask before generating. Match the **language** of the user's request and the title (the canonical example is in Spanish).

## Pillars → Nodes mapping

Use the **map-pillar-to-taxonomy** skill (`.cursor/skills/map-pillar-to-taxonomy/SKILL.md`) to resolve the ingressed pillars to X-Act nodes. That skill owns the matching rules and resolves each pillar to the most specific clear node — a **category** (`N`) or a **module** (`N.x`) — read from `taxonomies/xact-taxonomy.md`. Pillars often map to **modules** (e.g. "DevOps" → `1.2 DevOps`), not whole categories.

Interview-specific constraint: this guide needs **exactly one** node per pillar, because **each resolved node becomes one numbered sub-dimension**, in the order the pillars were given.

- If the mapping skill returns **more than one** node for a pillar, **ask the user** to pick the single node to use for that pillar's sub-dimension.
- If it returns **none** clearly, **ask the user** which node applies (offer the closest options).
- **Duplicate = same node.** Distinct pillars that share a parent category but resolve to **different modules** (e.g. `1.1 Architecture Quality` and `1.2 DevOps`) are **not** duplicates. Flag a duplicate only when two pillars resolve to the exact same node.
- Record each resolved node ID; it anchors that branch's downstream IDs.

## Source of truth

Read the X-Act hierarchy from `taxonomies/xact-taxonomy.md` and the criteria detail in `maturity-scores.md` at the project root. Use `interview-example.md` (in this skill folder) as the **format reference**.

## Mapping: X-Act → interview (REQUIRED)

The **resolved node is the sub-dimension's scope.** Its **direct children** become the criterios (module-level blocks); questions come from the scored level inside each branch. Note the interview's **Criterio** level is a module or sub-module — it is **not** the X-Act **parameter** (4th taxonomy level), which only appears as a question theme or as question context.

| Pillar resolves to | Sub-dimension scope | Criterio (children) | Question theme |
|--------------------|---------------------|----------------------|----------------|
| Category `N` | the whole category | each module `N.x` | scored level under each module |
| Module `N.x` | that one module | each sub-module `N.x.y` | scored level under each sub-module |

- Each resolved node is **one sub-dimension**, in pillar input order.
- **The question theme is the level where maturity is actually defined**, not a fixed level:
  - If maturity is defined at **sub-module** level (scores under `#### 1.1.1`), the **sub-module** is the question theme → one open question per sub-module, derived from the sub-module's scores. If the sub-module has parameters without their own maturity (marked _Using maturity from sub-module_, e.g. `1.1.1.1 Components`, `1.1.1.2 Dependencies`), use them as **context**: the question and its probes should touch the aspects those parameters name. A sub-module with no parameters at all (e.g. `1.4.1 Readability`) works the same way, minus the parameter context.
  - If maturity is defined at **parameter** level (scores under `##### 1.2.1.1`), each scored **parameter** is its own question theme → one open question per parameter.
  - A module may mix both: some sub-modules scored at sub-module level, others scored at parameter level. Pick the scored level per branch.
- Determine the scored level by reading `maturity-scores.md`: the lowest heading that carries `**Score 1..5**` bullets is the question theme.
- **WIP handling — judge by content, not by marker text.** A level is unscored only when it has **no usable score paragraphs**: its heading carries a level-wide WIP note (any wording, e.g. `_WIP — sub-modules to be defined_`) or **every** score bullet is WIP. A level where only **some** scores are WIP (e.g. `1.4.1 Readability` defines Scores 1, 3, 5) **is scorable** — derive the question from the defined scores only. For fully unscored levels, never invent a question — add a missing-maturity note instead (see [Question-writing rules](#question-writing-rules)).
- **Node absent from `maturity-scores.md` entirely.** A pillar may resolve to a node with **no coverage at all** in `maturity-scores.md` (the file currently covers only category `1. Software Engineering` — e.g. `3. Data Platform` or `10.2 Stakeholder Alignment` have no scores). Still emit the sub-dimension in pillar order, but do **not** invent criterios or questions: write its objective, then a missing-maturity note in the output language, e.g. *"Definición de madurez pendiente para este nodo en `maturity-scores.md` — preguntas no generadas."* Also tell the user in chat which pillars were affected.

## Output structure

Write to `interviews/{kebab-title}.md` (e.g. `interviews/tecnologia-y-herramientas.md`). Follow this template:

```markdown
# {Title} — Ejemplo de entrevista

> **Tipo de documento:** Ejemplo de guion de entrevista (assessment).
>
> {1–2 sentences framing this as an open-ended technical-assessment conversation with the organization's technology/engineering/product leaders — not a closed questionnaire.}
>
> **Cómo usar esta guía:**
> - Recorre las subdimensiones en orden; cada una abre con su objetivo de evaluación.
> - Usa los criterios como bloques temáticos y las preguntas como disparadores de conversación.
> - Profundiza con repreguntas para obtener evidencia, no solo percepciones.
> - {Goal restated here.}

| Nivel | Elemento | Descripción |
|-------|----------|-------------|
| 1.º | Subdimensión | Área temática que se explora durante la entrevista |
| 2.º | Criterio | Bloque de preguntas dentro de una subdimensión |
| 3.º | Pregunta | Pregunta abierta para guiar la conversación |

---

## Subdimensión 1: {Resolved node name for pillar 1 — category or module}

{Sub-dimension objective — derived from the goal + the resolved node's scope.}

### Criterio 1.1: {Child node name — module if pillar→category, sub-module if pillar→module}

- **{Scored-level name}:** {open-ended question derived from that level's maturity criteria}
- **{Scored-level name}:** {open-ended question}

### Criterio 1.2: {Child node name}

- **{Scored-level name}:** {open-ended question}

---

## Subdimensión 2: {Resolved node name for pillar 2}
...

---

## Cierre: Mapeo de dolores

> Bloque de síntesis (no puntuado). Úsalo al final para consolidar y priorizar los dolores detectados a lo largo de la entrevista.

- **Principales dolores:** De todo lo que conversamos{ — menciona brevemente los temas de las subdimensiones —}, ¿cuáles son los **3 dolores** que más les frenan hoy? Para cada uno, ¿qué impacto tiene (tiempo perdido, defectos, retrabajo, riesgo) y qué tan grande sería el apalancamiento de resolverlo frente al esfuerzo que implica?
```

One sub-dimension per ingressed pillar, in the order given.

## Closing block (REQUIRED)

End every guide with a **Cierre: Mapeo de dolores** synthesis section after the last sub-dimension. It is **not scored** — its job is to consolidate and prioritize the pains surfaced during the interview, framed through the Effective Engineering lens (leverage = impact ÷ time).

- Keep the heading and the *"Bloque de síntesis (no puntuado)…"* note.
- Ask for the **top 3 pains** that slow the team down today, and for each one its **impact** (tiempo perdido, defectos, retrabajo, riesgo) and the **leverage of fixing it vs. the effort** required.
- Tailor the "De todo lo que conversamos…" lead-in to recall the actual sub-dimension themes covered in this guide.
- Translate the labels when the output language isn't Spanish.

The template's fixed labels ("Ejemplo de entrevista", "Cómo usar esta guía", "Subdimensión", "Criterio", "Pregunta", the level table) are canonical in **Spanish**. When the output language isn't Spanish, **translate them** along with the rest of the document.

## Question-writing rules

Every question is **derived from the maturity criteria** of its scored level — not invented freely. The goal is that the interviewee's answer reveals **where on the Score 1→5 scale** the organization sits.

How to derive a question from maturity:
1. Read the **Score 1..5** paragraphs for the scored level (sub-module or parameter) in `maturity-scores.md` — all that are defined (some bullets may be WIP).
2. Identify the **discriminators** — the dimensions that change as the score rises (e.g. % automated, deploy frequency, manual approvals, ownership model, tooling standardization).
3. Write **one open-ended question per scored level** that probes those discriminators, so the answer can be placed on the scale. Never reveal the scores or ask "what score are you" — ask about reality.
4. Add concrete probes drawn from the score wording ("¿qué porcentaje?", "¿con qué frecuencia?", "¿cuántas aprobaciones manuales?", "¿puedes darme un ejemplo?").

Rules:
- Questions are **open-ended** — they ask the interviewee to *describe*, *explain*, or *give examples*, never yes/no.
- One bold topic lead-in per question, matching the name of the scored level (sub-module or parameter).
- A question must touch the **key discriminators** so a 1 and a 5 would answer it very differently.
- When maturity lives at the **sub-module** and its parameters have none of their own, the parameters are **context, not separate questions**: weave the aspects they name (e.g. components, dependencies, data model) into the sub-module question's probes.
- Incomplete maturity — two distinct cases:
  - **Some scores WIP, others defined** → write the question from the **defined** scores; the available endpoints still give the discriminators.
  - **All scores missing/WIP** → do **not** invent a question or content. Keep the level's bold lead-in and add a note in the output language stating the maturity definition is missing, e.g. *"**{Nombre del nivel}:** Definición de madurez pendiente — pregunta no generada."*
- Keep the interviewee's industry/context in mind if the user supplied one.

### Effective Engineering lens (REQUIRED)

Every question must be framed through the principles of **"The Effective Engineer" (Edmond Lau)** — engineering effectiveness is **leverage = impact produced ÷ time invested**. The maturity criteria define *what* to probe; this lens shapes *how* you probe it, so answers reveal whether the organization invests in high-leverage practices, not just whether a tool exists.

Apply these high-leverage themes when phrasing the question and its probes (use the ones relevant to the scored level):
- **Iteration speed** — how fast can they build, test, and ship? Are feedback loops short?
- **Optimizing for learning** — do they treat work as a chance to learn and improve, run retros, share knowledge?
- **Prioritizing high-leverage work** — do they focus effort where impact is highest, or spread thin / firefight?
- **Measuring what matters** — do they instrument and use metrics to drive decisions, or rely on gut feel?
- **Validating early and often** — do they de-risk with early feedback, prototypes, small batches?
- **Minimizing operational burden** — do they automate toil, reduce on-call/manual load, and build to simplify?
- **Investing in the team & long-term** — onboarding, documentation, balancing quick wins vs. compounding investments.

Practically: when a maturity discriminator could be probed either as "do you have X?" or "how much leverage does X give you?", **always choose the leverage framing**. Add a probe that surfaces the impact-vs-effort trade-off (e.g. "¿cuánto tiempo les ahorra?", "¿qué decisiones cambian con esa métrica?", "¿qué trabajo manual eliminó?").

**Example — deriving from maturity (`1.2.1.2 Deployment`):**

Score 1 = manual, monthly, downtime, freeze during peaks → Score 5 = on-demand several times/day, zero downtime, business-controlled. Discriminators: deploy frequency, downtime, who decides, peak-period freezes.

→ Question: *"**Despliegue a producción:** ¿con qué frecuencia despliegan (varias veces al día, mensual, trimestral), hay ventana de downtime, y quién decide cuándo se libera — el negocio o restricciones de TI? ¿Existen congelamientos en picos de tráfico?"*

## Workflow

1. Confirm title, pillars (list), and goal.
2. Resolve each pillar to one X-Act node (category `N` or module `N.x`) — see [Pillars → Nodes mapping](#pillars--nodes-mapping).
3. For each resolved node, look up its children in `maturity-scores.md` (modules if a category, sub-modules if a module). For each branch, find the **scored level** (sub-module vs parameter) — see mapping rules. If a node has **no coverage** in `maturity-scores.md`, emit its sub-dimension with a missing-maturity note instead of questions and inform the user.
4. Generate one open question per **scored level**, **derived from that level's Score 1..5 discriminators** and framed through the **Effective Engineering lens** (leverage = impact ÷ time) — see [Question-writing rules](#question-writing-rules).
5. Write the file using the template above — one sub-dimension per pillar, in input order; verify language and numbering are consistent.

## Checklist

- [ ] Every pillar resolved to exactly one X-Act node — category or module (asked the user if ambiguous; duplicates flagged only on same node)
- [ ] One sub-dimension per pillar, in input order, scoped to the resolved node
- [ ] Interview scope covers the children under each resolved node (modules of a category, or sub-modules of a module)
- [ ] One open-ended question per scored level (sub-module or parameter, per where maturity is defined); sub-module questions use unscored parameters as context in their probes
- [ ] Each question derived from that level's Score 1..5 discriminators (a 1 vs a 5 would answer differently)
- [ ] Each question framed through the Effective Engineering lens (leverage/impact-vs-effort, not just "do you have the tool?")
- [ ] Partially-WIP levels kept, questions derived from their defined scores; fully unscored levels carry a missing-maturity note in the output (no invented questions)
- [ ] Pillars whose node is absent from `maturity-scores.md` get a sub-dimension with a missing-maturity note (no invented criterios/questions) and the user was informed
- [ ] Header includes type, framing, "Cómo usar", and the goal
- [ ] Ends with the unscored "Cierre: Mapeo de dolores" synthesis block (top 3 pains, impact, leverage-vs-effort), lead-in tailored to the sub-dimensions covered
- [ ] Output language matches the title/request, including the template's fixed labels
- [ ] Sub-dimensions and criterios numbered sequentially
