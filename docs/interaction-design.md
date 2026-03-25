# Interaction Design — PolyLine Editor (Phase 3)

## 1) Design goals
- Learnable in < 2 minutes using help overlay
- Prevent accidental edits via mode-based actions + hover preview
- Provide continuous feedback (mode badge + status bar + hover highlight)

## 2) User actions (teacher scenario)
Keyboard verbs + mouse interaction:
- `B` begin: start new polyline
- click: add point in draw mode
- `M` move: drag closest point
- `D` delete: remove closest point
- `R` refresh: clear & redraw from model
- `Q` quit: exit/clear/reset (web decision must be consistent across UI)

## 3) Modes (state model)
Modes:
- Draw
- Move
- Delete
- Insert (extension)

### State transitions (dialog notation)
- `B` → Draw (creates new polyline, sets active)
- `M` → Move
- `D` → Delete
- `I` → Insert
- `Esc` → Draw (cancel/escape)
- `F` or double-click → Finish polyline (if ≥ 2 points)

## 4) Feedback rules
- Always show mode in header badge + stats “Mode”
- Show status message after every action:
  - begin, add point, finish, move, delete, insert, save, load, clear, exit
- Hover preview before commit:
  - Move/Delete: ring highlight of target vertex
  - Insert: highlight projection point on segment
  - Draw: show dashed preview line from last point to cursor

## 5) Error prevention rules
- Confirm dialogs for destructive actions (clear all, delete polyline, exit)
- Finish polyline only if ≥ 2 points
- Use thresholds (e.g., 20px for nearest point) to reduce mis-selection

## 6) Consistency checks (must align)
- Help overlay shortcuts must match real key bindings
- Tip panel (“Press Q to quit/clear”) must match quit behavior
