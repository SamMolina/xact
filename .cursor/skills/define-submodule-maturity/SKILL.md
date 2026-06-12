---
name: define-submodule-maturity
description: >-
  Adds or updates X-Act maturity criteria at sub-module level in maturity-scores.
  Use when the user asks to define maturity for a sub-module, pass maturity at
  sub-module level, assign maturity scores, or provides score paragraphs for an
  X-Act ID like 1.1.2.
---

# Define Sub-Module Maturity (X-Act)

## Target file

All edits go to `maturity-scores` at the project root.

## Hierarchy (markdown headings)

| X-Act level | ID example | Heading |
|-------------|------------|---------|
| 1st — Category | `1` | `## 1. Software Engineering` |
| 2nd — Module | `1.1` | `### 1.1 Architecture Quality` |
| 3rd — Sub-module | `1.1.2` | `#### 1.1.2 API Strategy` |
| 4th — Parameter | `1.1.2.1` | `##### 1.1.2.1 Standards` |

Maturity criteria may live at **sub-module** (`1.1.2`) or **parameter** (`1.1.2.1`) level. This skill covers **sub-module** level only.

## Workflow

1. **Locate** the sub-module heading: `#### {id} {name}`.
2. **Insert scores** immediately under that heading, **before** any `#####` parameter headings.
3. **Update child parameters** — replace `_WIP — maturity scores to be defined_` with `_Using maturity from sub-module_` for every parameter under that sub-module.
4. **Do not** add parameter-level score bullets when maturity is defined at sub-module level.
5. **Preserve** existing content outside the target sub-module.

## Score format

Use exactly five scores, ascending from lowest to highest maturity:

```markdown
#### 1.1.2 API Strategy

*   **Score 1:** {lowest maturity description}
*   **Score 2:** {description}
*   **Score 3:** {description}
*   **Score 4:** {description}
*   **Score 5:** {highest maturity description}

##### 1.1.2.1 Standards
_Using maturity from sub-module_
```

Rules:
- One bullet per score; paragraph text on the same line after `**Score N:**`.
- Keep user wording verbatim unless fixing obvious duplicates or typos.
- Preserve reference citations when present (e.g. `[1]`, `[2]`).
- If a score level has no paragraph in the source, leave it as `_WIP — maturity scores to be defined_` or ask the user.

## Parsing user input

Users often paste **paragraph first, score number after**. The number written immediately **after** a paragraph block is that paragraph's score label — map it **literally** to that `**Score N:**`. Then reorder to **Score 1 → Score 5** in the file.

| User label | File placement |
|------------|----------------|
| `1` (worst) | `**Score 1:**` |
| `2` | `**Score 2:**` |
| `3` | `**Score 3:**` |
| `4` | `**Score 4:**` |
| `5` (best) | `**Score 5:**` |

**Do not remap by maturity intent.** Trust the user's explicit numbers even when a block's content sounds more (or less) advanced than its label suggests. Example: a paste of four blocks labeled `4`, `3`, `2`, `1` maps to Scores 4, 3, 2, 1 respectively — even if the block labeled `4` reads like a top-tier "5".

**Missing levels stay WIP — never shift content to fill a gap.** If a score level has no paragraph (e.g. no `5` label was provided), leave that level as `_WIP — maturity scores to be defined_`. Do not promote/demote other blocks to cover it.

When labels are genuinely ambiguous (duplicate numbers, no numbers at all), ask the user or map by maturity intent and note your assumption.

## Sub-module without parameters

Some sub-modules have no 4th-level parameters (e.g. `1.4.1 Readability`). Add scores directly under the `####` heading only.

## Parameter-level maturity (out of scope)

If the user provides scores for a specific parameter ID (e.g. `1.6.3.1`), place bullets under that `#####` heading instead. Do **not** mark sibling parameters as *Using maturity from sub-module* unless the parent sub-module also has its own scores.

## Checklist

- [ ] Scores are under `#### {sub-module id}`, not under `#####` parameters
- [ ] Scores ordered 1 (lowest) through 5 (highest)
- [ ] Each paragraph mapped to its **literal** user-supplied label (not remapped by maturity intent)
- [ ] Any level without a supplied paragraph left as `_WIP_` (no content shifted to fill it)
- [ ] All child parameters say `_Using maturity from sub-module_`
- [ ] Sub-module ID and parameter IDs match the X-Act hierarchy
- [ ] No unrelated sections changed

## Examples in maturity-scores

- `1.1.1 Architectural Style` — sub-module scores + parameters inherit
- `1.1.2 API Strategy` — sub-module scores + parameters inherit
- `1.7.1.3 Solution Development` — parameter-level scores, labeled `4`/`3`/`2`/`1` → Scores 4/3/2/1, Score 5 left as `_WIP_`
