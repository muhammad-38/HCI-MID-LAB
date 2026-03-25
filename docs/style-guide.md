# Style Guide — PolyLine Editor (Phase 3)

## Typography
- Display headings: Syne (bold)
- UI text: DM Mono (monospace)

## Color system
- Background: #0e0f11
- Surfaces: #161820, #1c1e26
- Border: #2a2d38
- Accent: #4f8ef7
- Success: #3ecf8e
- Warning (move): #f5a623
- Danger (delete): #f46a6a
- Text: #d8dce8
- Muted: #5c6480

## Components
### Mode badge
- Default: accent background
- Move: amber background (high salience)
- Delete: red background (danger)

### Buttons
- Primary: accent
- Warning: amber
- Danger: red
- Success: green
- Hover: raise contrast
- Active: scale down slightly for tactile feedback

### Sidebar list items
- Selected polyline: tinted accent background + border
- Include color dot + point count + delete icon

## Motion/feedback
- Toast appears briefly after save/load/exit
- Hover highlight indicates target selection (move/delete/insert)
