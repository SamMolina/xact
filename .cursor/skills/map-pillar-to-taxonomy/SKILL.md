---
name: map-pillar-to-taxonomy
description: >-
  Matches one or more ingressed X-Act pillars (the user's business-facing terms
  such as "Engineering Practices", "DevOps", "Architecture") to the most specific
  X-Act node — a category (N) or a module (N.x) — from taxonomies/xact-taxonomy.md.
  Use when the user asks to map pillars to categories or modules, match a pillar
  to the X-Act taxonomy, resolve pillars, or figure out which X-Act area a pillar
  covers.
---

# Map Pillar to Taxonomy (X-Act)

Resolves each ingressed **pillar** to the most specific matching X-Act node: a **category** (`N`) or a **module** (`N.x`) in `taxonomies/xact-taxonomy.md`. A pillar is the user's business-facing term; it often corresponds to a **module**, not the whole category.

## Inputs (ask if missing)

1. **Pillars** — one or more pillars to map. Accept a list (e.g. "Engineering Practices", "DevOps", "Architecture").

Match the **language** of the user's request in any rationale text.

## Source of truth

Read the hierarchy from `taxonomies/xact-taxonomy.md` at the project root — both categories (`N`) and their modules (`N.x`). Confirm against it before mapping. Canonical category list:

| # | Category |
|---|----------|
| 1 | Software Engineering |
| 2 | Product and Design |
| 3 | Data Platform |
| 4 | Operational Efficiency |
| 5 | Cloud Platform |
| 6 | Talent Development |
| 7 | Talent Acquisition |
| 8 | Security |
| 9 | Industry 4.0 |
| 10 | Change Management |
| 11 | AI Maturity |
| 12 | Org Design |

Modules live one level under each category (e.g. `1.1 Architecture Quality`, `1.2 DevOps`, `1.6 Engineering Excellence`). Read them from the taxonomy, do not assume.

## Mapping rules

- Match each pillar by **exact name, synonym, or clear semantic fit**.
- **Resolve to the most specific node that clearly fits.** Prefer a **module** (`N.x`) when the pillar maps to a specific module; use the **category** (`N`) only when the pillar spans the whole category.
  - "DevOps" → **module** `1.2 DevOps` (within `1. Software Engineering`).
  - "Architecture" → **module** `1.1 Architecture Quality`.
  - "Engineering Practices" → **module** `1.6 Engineering Excellence`.
  - A broad pillar like "Software Engineering" → **category** `1. Software Engineering`.
- A pillar may resolve to **more than one** node if it clearly spans several. List the **primary** node first.
- **Duplicate rule — compare the resolved node, not its parent.** Several pillars may share a parent category yet map to **distinct modules** — this is normal and is **not** a duplicate. Flag a duplicate only when two pillars resolve to the **same node** (same module, or same category).
- Resolve **every** pillar. If a pillar maps to **none** clearly, ask the user which node it corresponds to (offer the closest options).

## Output format

Present the result as a table, in the order pillars were given:

```markdown
| Pillar | X-Act Match (category or module) | Level | Rationale |
|--------|----------------------------------|-------|-----------|
| {pillar} | {N.x Module} or {N. Category} | module / category | {exact / synonym / semantic fit} |
```

If any pillar was ambiguous and you asked the user, reflect their chosen node in the final table.

## Workflow

1. Confirm the list of pillars (ask if none provided).
2. Read `taxonomies/xact-taxonomy.md` to confirm current categories and modules.
3. Map each pillar to the most specific clear node (module `N.x` preferred, category `N` when it spans the whole category).
4. For unmappable pillars, ask the user before finalizing.
5. Output the mapping table in input order.

## Checklist

- [ ] Every pillar appears in the output table, in input order
- [ ] Each pillar resolved to the most specific clear node (module preferred over category)
- [ ] Node IDs/names match `taxonomies/xact-taxonomy.md`
- [ ] Duplicates flagged only when two pillars hit the **same node** (shared parent category is not a duplicate)
- [ ] Ambiguous/unmappable pillars resolved by asking the user
- [ ] Rationale notes exact / synonym / semantic fit
