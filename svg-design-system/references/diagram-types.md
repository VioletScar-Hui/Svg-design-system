# Diagram types — selection + recipes

Pick the form from the **content's structure**, not habit. For each type below: when to use, how to lay
it out, and how it carries the **5 information levels** (L1 topic · L2 modules · L3 relations · L4
takeaway · L5 memory hook). Every diagram must satisfy all five — see SKILL.md.

## How to choose (decision order)

Ask in this order; stop at the first match:

1. Is it a **closed loop** (output feeds back to input)? → **循环图 Cycle**
2. Is it ordered by **time / steps / causality**? → **流程图 Flowchart** (or **时间轴 Timeline** if the
   axis is calendar time / milestones)
3. Is it **two independent dimensions** crossed? → **矩阵图 Matrix**
4. Is it **A vs B** weighed against each other? → **对比图 Comparison**
5. Is it **layers / containment / system composition**? → **架构图 Architecture**
6. Is it **many-to-many links** among entities? → **关系/节点图 Network**

If two fit, name the trade-off to the user and let them choose.

---

## 1. 流程图 Flowchart

**Use when:** sequential steps, pipelines, decision branches (输入→处理→输出, 先A后B).

**Layout:** left→right (or top→bottom) lane of node boxes, connected by accent arrows. Branch with a
diamond/decision node. Keep ≤6 primary steps; group sub-steps inside a node.

- L1 title above the lane · L2 the step boxes · L3 the directional arrows (direction = the message) ·
  L4 highlight the critical/bottleneck step in accent · L5 an icon on the start or end node.

## 2. 矩阵图 Matrix

**Use when:** classifying/comparing along two independent axes — 2×2, priority (effort×impact), quadrants.

**Layout:** two perpendicular axes with labeled poles; four quadrant zones (tint with low-opacity fills);
place items as dots/chips. Label each quadrant.

- L1 title + the two axis names · L2 the quadrant labels · L3 the axes themselves (the relation is
  position) · L4 highlight the "winning" quadrant or a key item in accent · L5 the quadrant tints.

## 3. 架构图 Architecture

**Use when:** system composition, layers, modules and their static relationships (前端/后端/数据层…).

**Layout:** horizontal layers stacked top→bottom, each layer a rounded container holding module boxes;
data/control flow shown with thin connectors. Nest containers to show "belongs to".

- L1 system name · L2 the module boxes · L3 nesting + connectors between layers · L4 highlight the core
  module / critical path in accent · L5 a distinctive shape for the "brain"/core component.

## 4. 时间轴 Timeline

**Use when:** evolution, roadmap, milestones along calendar time.

**Layout:** one horizontal spine; evenly spaced milestone markers; alternate labels above/below to avoid
crowding. Date in `.mono .tiny`.

- L1 title (what journey) · L2 the milestone markers · L3 the spine + ordering · L4 emphasize the
  pivotal milestone (the "now" or turning point) in accent · L5 a marker shape that stands out.

## 5. 关系/节点图 Network

**Use when:** many-to-many relationships, ecosystems, stakeholder maps — no single direction.

**Layout:** central or radial nodes connected by lines; line weight = relationship strength. Avoid
crossing where possible; cluster related nodes. Keep ≤8 nodes or it turns to spaghetti.

- L1 title · L2 the nodes · L3 the connecting lines (weight/style encodes type) · L4 enlarge/accent the
  hub or key node · L5 the overall constellation shape.

## 6. 循环图 Cycle

**Use when:** a closed, repeating loop — Agent loop, PDCA, growth flywheel, feedback systems.

**Layout:** 3–6 stages around a ring, curved accent arrows flowing one direction; a label/icon in the
center naming the loop.

- L1 the loop's name (center) · L2 the stages · L3 the circular arrows (the "it repeats" message) · L4
  accent the stage where leverage/compounding happens · L5 the ring itself as the memory hook.

## 7. 对比图 Comparison

**Use when:** A vs B, before/after, old way vs new way.

**Layout:** two columns (or split panel) sharing aligned rows of criteria; use ink for the baseline side
and accent for the favored side. A center divider.

- L1 title (what's compared) · L2 the two sides + the criteria rows · L3 row-by-row alignment (the
  relation is "same dimension, different value") · L4 accent the decisive difference · L5 a check/cross
  or a clear visual asymmetry.

---

## After drawing — the 5-level self-check (do not skip)

Point at where each level lives. If you can't point at it, it's missing:

- [ ] **L1** — one glance tells me the topic?
- [ ] **L2** — the core modules are obvious and countable?
- [ ] **L3** — I can read how they relate from arrows/layout alone?
- [ ] **L4** — there is exactly one clear takeaway, in accent?
- [ ] **L5** — there's one thing I'll remember tomorrow?

A common failure is **L4 inflation**: too many things emphasized, so nothing is. Accent = one idea.
