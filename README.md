# X-Act

X-Act is a technical-assessment framework used to gauge an organization's engineering maturity. This repository holds the framework's source of truth — its taxonomy and maturity criteria — together with a set of Cursor skills that turn that data into assessment interview guides and keep the maturity definitions up to date.

> The interviews produced here assess **an organization's** technical maturity by talking to its technology, engineering, and product leaders. They are **not** candidate/job interviews.

## How it fits together

```
pillars (business terms)  ──map-pillar-to-taxonomy──▶  X-Act node (category N / module N.x)
X-Act node + maturity-scores.md  ──create-interview──▶  interview guide in interviews/
score paragraphs  ──define-submodule-maturity──▶  maturity-scores.md
```

The X-Act hierarchy has five levels:

| Level | Element   | Example                                   |
|-------|-----------|-------------------------------------------|
| 1st   | Category  | `1. Software Engineering`                 |
| 2nd   | Module    | `1.2 DevOps`                              |
| 3rd   | Sub-module| `1.2.1 Continuous Integration and Deployment` |
| 4th   | Parameter | `1.2.1.2 Deployment`                      |
| 5th   | Question  | *(not contemplated yet in taxonomy)*                  |

Maturity criteria (Score 1 → 5) are defined at the **sub-module** or **parameter** level, depending on the granularity needed.

## Repository layout

| Path | Purpose |
|------|---------|
| `taxonomies/xact-taxonomy.md` | The X-Act hierarchy (categories → modules → sub-modules → parameters). Hierarchy only, no scores. |
| `taxonomies/arch-assessment-taxonomy.md` | The Architecture Assessment (`AA.*`) sensible-defaults taxonomy. |
| `maturity-scores.md` | The Score 1–5 maturity criteria for X-Act nodes. The detailed source of truth for question generation. Work in progress — currently covers category `1. Software Engineering`. |
| `sensible-defaults.md` | Maps Architecture Assessment sensible defaults (`AA.*`) onto the X-Act hierarchy. |
| `.cursor/skills/create-interview/interview-example.md` | Canonical format reference for a generated interview guide (Spanish), used by the `create-interview` skill. |
| `interviews/` | Generated interview guides plus `interview-prompts.md`, a log of the inputs used to produce each one. |
| `.cursor/skills/` | The Cursor skills that operate on the framework (see below). |

## Skills

These live under `.cursor/skills/` and are invoked from Cursor.

- **`map-pillar-to-taxonomy`** — resolves a business-facing pillar (e.g. "DevOps", "Architecture") to the most specific X-Act node, a category `N` or a module `N.x`.
- **`create-interview`** — generates an open-ended assessment interview guide from a title, one or more pillars, and a goal. Each pillar becomes one sub-dimension; questions are derived from the maturity criteria so an interviewee's answer places the organization on the Score 1→5 scale, framed through *The Effective Engineer*'s leverage lens. Output is written to `interviews/{kebab-title}.md`.
- **`define-submodule-maturity`** — adds or updates Score 1–5 criteria at the sub-module level in `maturity-scores.md`.

## Typical workflow

1. Decide which areas (pillars) to assess and the interview's goal.
2. Use `map-pillar-to-taxonomy` to resolve each pillar to an X-Act node.
3. Use `create-interview` to generate the guide into `interviews/`, recording the inputs in `interviews/interview-prompts.md`.
4. As maturity definitions firm up, use `define-submodule-maturity` to fill in `maturity-scores.md`.

## Conventions

- Interview guides are written in the language of the request (the canonical example and existing guides are in Spanish).
- Maturity scores ascend from Score 1 (lowest maturity) to Score 5 (highest). Undefined levels are marked `_WIP — maturity scores to be defined_` and are never filled with invented content.
