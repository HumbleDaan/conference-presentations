# Conference Presentations Repository

## Purpose
This repository contains design assets and materials for conference presentations, primarily focused on Microsoft Fabric capacity-related topics.

## Repository Structure

### capacities/
Design assets for Fabric Capacities presentations.

#### capacities/icons/
SVG icon set for capacity visualization and presentations. All icons use transparent backgrounds.

**SKU Grid Icons:**
- `f2-grid.svg` through `f2048-grid.svg` - Visual grids representing different Fabric capacity SKUs (F2, F4, F8, F16, F32, F64, F128, F256, F512, F1024, F2048)
- Used to visualize capacity unit distributions across different SKU sizes

**Timeline Bar Icons:**
- `bar-interactive.svg` - Red bar for interactive operations (5-minute smoothing)
- `bar-background.svg` - Blue bar for background operations (24-hour smoothing)
- `bar-stacked.svg` - Combined stacked bar showing both operation types

**Quota Bar Icons:**
- Located in `capacities/icons/quota-bars/`
- `cu-8.svg`, `cu-16.svg`, `cu-32.svg`, `cu-64.svg`, `cu-80.svg`, `cu-128.svg`
- Fixed width, variable height bars for quota visualization

**Other Icons:**
- `cu-block.svg` - Single capacity unit visual representation
- `window-30sec.svg` - 30-second evaluation window block

## Usage
These assets are designed for use in:
- PowerPoint/presentation slides
- Technical documentation
- Conference talks about Microsoft Fabric capacities
- Educational materials on capacity planning and monitoring

## Technology Stack
- SVG format for scalability and transparency support
- Git version control for asset management
- GitHub for collaboration and distribution
