# Challenges & Confusions (Phase 3)

1) Meaning of “Quit (Q)” in web context
- Decision: quit will either clear/reset state OR disable further input and show message.
- Must ensure UI tip + help overlay match the chosen behavior.

2) Refresh (R) vs automatic redraw
- Canvas redraw happens often; prompt still expects explicit refresh action.
- Ensure key binding and status message exist.

3) Undo design ambiguity
- Prompt doesn’t require undo; if included, it must be consistent and predictable.
