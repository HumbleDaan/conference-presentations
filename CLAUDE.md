# CLAUDE.md - Instructions for Claude Code

## Repository Purpose
Design assets for Microsoft Fabric conference presentations. Primary focus: capacity visualization and education.

## Design System

### Color Palette
When creating or modifying SVGs, use these exact colors:

| Color | Hex | Usage |
|-------|-----|-------|
| Fabric Teal | `#117865` | Primary capacity fill |
| Fabric Teal Dark | `#0D5A4C` | Strokes, borders, grid lines |
| Interactive Red | `#D13438` | Interactive operations (5-min smoothing) |
| Background Blue | `#0078D4` | Background operations (24-hr smoothing) |
| Success Green | `#107C10` | Healthy states |
| Warning Orange | `#A84D0A` | Throttling states (darkened for accessibility) |
| Power BI Yellow | `#F2C811` | **Fills only** - fails WCAG contrast for text |

### Critical Color Semantics
- **Red = Interactive** — spiky operations, urgent, 5-minute smoothing window
- **Blue = Background** — stable operations, calm, 24-hour smoothing window
- This matches the Capacity Metrics App exactly. Do not reverse these.

### SVG Conventions
- Always use transparent backgrounds (no white rect fills)
- Standard stroke-width: `1.5` for containers, `1` for grid lines, `2` for standalone blocks
- Border radius: `rx="4"` to `rx="8"` depending on size
- Grid line opacity: `0.6`
- Timeline bar opacity: `0.85`

### Scaling Conventions
- **Quota bars**: Fixed width 40px, height = CU × 2 (e.g., 64 CU = 128px)
- **SKU grids**: Cell size scales down for larger SKUs (24px for F2-F64, 14px for F128-F256, 8px for F512+)

## File Organization

```
capacities/
├── icons/
│   ├── cu-block.svg          # Single capacity unit
│   ├── f{N}-grid.svg         # SKU grids (F2 through F2048)
│   ├── bar-interactive.svg   # Red timeline bar
│   ├── bar-background.svg    # Blue timeline bar
│   ├── bar-stacked.svg       # Combined stacked bar
│   ├── window-30sec.svg      # 30-second evaluation window
│   └── quota-bars/           # Fixed-width bars for quota visualization
│       └── cu-{N}.svg        # Variable height by CU count
```

## When Creating New Assets

1. **Check existing colors** - reuse the palette above
2. **No text in icons** - keep icons text-free for flexibility in presentations
3. **Transparent backgrounds** - SVGs should import cleanly as icons in PowerPoint
4. **Test accessibility** - all colors except yellow pass WCAG AA (4.5:1) against white

## Presentation Context
These assets support a Fabric Capacities presentation (~82 slides) covering:
- CU to F64 capacity unit transitions
- Timeline visualization (30-second windows, smoothing)
- Quota and reservation stacking
- Bursting and throttling scenarios
