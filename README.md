# PolyLine Editor — Phase 3: Design

> **CS 555 Human Computer Interaction & Computer Graphics · 2026**  
> Take Home Lab Exercise — Group Exercise (4 Members)  
> Supervisor: Dr. Humera Tariq

---

## My Contribution — Phase 3: Design

This repository covers **Phase 3 of the interaction design process** (ref: Figure 5.1, Dix et al. Ch. 5).

Phase 3 sits between analysis and implementation. My job was to take the requirements and analysis from my teammates and produce a precise, implementable design specification — covering:

- UI layout and visual grammar
- Interaction mode specification (Draw / Move / Delete / Insert)
- State transition diagram
- Data structure design (polyline schema, JSON format)
- Algorithm specifications (nearest vertex, delete, insert-on-segment, snap-to-grid)
- HCI principles mapping (Nielsen's heuristics)
- Proposed extensions and known limitations

---

## Live Site

**[View Phase 3 Design Specification →](https://YOUR-USERNAME.github.io/polyline-editor-phase3/)**

The documentation site is built as a single `index.html` — no build step, no dependencies.

---

## Repository Structure

```
polyline-editor-phase3/
│
├── index.html          ← Phase 3 design documentation site (GitHub Pages)
├── README.md           ← This file
└── design/
    └── (supporting assets if any)
```

---

## How to Run Locally

Just open `index.html` in any modern browser:

```bash
# Option 1: Direct open
open index.html

# Option 2: Local server (to avoid CORS on fonts)
python -m http.server 8080
# then visit http://localhost:8080
```

No npm, no build, no install.

---

## Design Process Summary (Figure 5.1)

| Phase | Owner | Status |
|-------|-------|--------|
| Phase 1 — Requirements | Student A | ✅ Done |
| Phase 2 — Analysis | Student B | ✅ Done |
| **Phase 3 — Design** | **Me (Student C)** | **✅ This repo** |
| Phase 4 — Implement & Deploy | Student D | 🔗 [their repo] |

---

## Key Design Decisions & Justifications

### 1. Mode-based interaction
Chose persistent modes (Draw / Move / Delete / Insert) over transient tool-switching. Reasoning: matches the textbook specification (B, D, M, R, Q keys) and creates a clear mental model — one action per mode.

### 2. 20px hit radius for vertex selection
Direct application of **Fitts's Law** — vertex circles are visually small (r=4px) but the effective click area is 20px radius, making the target 5× larger than it appears. This significantly reduces pointing time and error rate.

### 3. Event-driven rendering (no animation loop)
The canvas redraws only on user events (mousemove, click, keydown). No `requestAnimationFrame` loop. This keeps CPU usage at ~0% when the user is idle — important for a drawing tool that may stay open for long sessions.

### 4. JSON save format with version field
The persistence format includes a `"version": 1` field so future implementations can detect and migrate older save files. All coordinates are stored as plain integers — no floating point drift between sessions.

---

## HCI Principles Applied

| Nielsen Heuristic | Design decision |
|---|---|
| H1 — Visibility of system status | Status bar, mode badge, preview line, hover ring |
| H2 — Match with real world | Vertices appear where clicked; pixel coordinates shown |
| H3 — User control & freedom | Esc resets mode; confirm on clear-all |
| H4 — Consistency & standards | Keyboard shortcuts match textbook spec exactly |
| H6 — Recognition over recall | Toolbar shows all modes + key labels; Help overlay |
| H7 — Flexibility & efficiency | Experts use keyboard; beginners use toolbar |

---

## Challenges & Confusions

Listed honestly as the teacher encouraged:

1. **Mode vs. tool mental model** — Should Delete/Move be persistent modes or held keys? Chose persistent to match spec, but tool-style (hold key = activate, release = return) would feel more fluid for power users.

2. **Hit threshold calibration** — 20px for vertices, 15px for segments were chosen empirically. The correct solution for a production tool would be a spatial index (quadtree) with zoom-aware thresholds.

3. **No undo in the spec** — Delete is irreversible in the base spec. This is a real usability gap. Flagged it as a known limitation and proposed an undo stack as a priority extension (deep-copy `polys[]` before each mutation).

4. **Canvas coordinate system on resize** — Canvas pixel dimensions are separate from CSS layout dimensions. Without explicit sync, resizing the window stretches all drawings. Resolved via ResizeObserver, at the cost of clearing the canvas — which is why JSON save/load became essential.

---

## References

- Dix, A., Finlay, J., Abowd, G. D., & Beale, R. (2004). *Human-Computer Interaction* (3rd ed.). Pearson. Ch. 5.
- Nielsen, J. (1994). *Usability Engineering*. Morgan Kaufmann.
- Norman, D. A. (2013). *The Design of Everyday Things* (Revised ed.). Basic Books.
- Foley, J. et al. (1995). *Computer Graphics: Principles and Practice* (2nd ed.). Addison-Wesley. — PolyLine Editor spec adapted from exercises herein.
- MDN Web Docs. Canvas API. https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API

---

*Submitted: 26 March 2026 · CS 555 HCI-CG 2026*
