# Accessibility — PolyLine Editor (Phase 3)

## Keyboard accessibility
- All main actions are available via keyboard shortcuts (B, M, D, I, F, S, L, R, Q, Esc).
- Ensure buttons are reachable by Tab and show visible focus.

## Screen-reader / ARIA suggestions
- Add `aria-label` on icon-only delete buttons (✕).
- Ensure help overlay has proper focus handling (trap focus when open, Esc closes).

## Contrast / readability
- Ensure muted text still readable on dark background.
- Ensure mode colors (amber/red) remain legible for color vision deficiencies by using text labels, not color alone.

## Error prevention
- Confirm dialogs for destructive actions.
- Status messages for every action (feedback).
