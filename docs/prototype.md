# Prototype — PolyLine Editor (Phase 3)

## Prototype type
Medium-fidelity prototype implemented directly in HTML/CSS (Canvas UI) + documented interactions.

## Screens to capture (add to docs/images)
1. Default state (no polylines)
2. Draw mode while drawing (preview dashed line visible)
3. Move mode hover highlight + dragging
4. Delete mode hover highlight
5. Insert mode (segment projection dot visible)
6. Help overlay open
7. Save/Load toast feedback
8. Exit confirmation dialog

## Add images
Place screenshots in `docs/images/` and reference them here, e.g.:
- `docs/images/draw-mode.png`
- `docs/images/help-overlay.png`

## Design improvements (proposed)
- Ensure `R` refresh is actually implemented to match help text.
- Ensure `Q` quit/clear behavior matches tip + help.
- Add clear keyboard focus outline for toolbar buttons (accessibility).
- Add small “active polyline” label to reduce confusion.
