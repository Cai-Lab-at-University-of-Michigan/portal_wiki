---
tags:
   - annotation
   - flood-filling
   - segmentation
   - algorithm
---

*This tutorial guides the process for using the Flood Fill algorithm for interactive 3D neuron segmentation.*

---

## Overview

**Flood Fill** is an interactive region-growing segmentation algorithm. Place seed points on the structure you want to segment, and the algorithm grows outward from each seed based on intensity similarity. Negative seeds can remove over-segmented regions.

---

## Getting Started

1. Open an image scene and select a **segmentation layer** in the right sidebar
2. Open the **Interactive Annotation** panel
3. Click **Lock View** to freeze the current viewport — this defines the region the algorithm operates on
4. Select the **Algorithm** tool, then choose **Flood Fill**

> Lock a tight region of interest for faster computation. To change the region, **Unlock**, navigate, then **Lock View** again.

---

## Place Positive Seeds

1. Ensure **+ Add** mode is selected (green button)
2. Click on the viewer to place seeds on the structure to segment
3. The algorithm runs automatically after each seed placement

Seeds appear as numbered entries (+1, +2, +3) in the seed list, each with its own tolerance.

---

## Adjust Tolerance

Tolerance controls how aggressively the region grows (0.0 = exact match, 1.0 = grows everywhere).

- **New seeds**: Adjust the **New Seed Tolerance** slider *before* placing a seed (default: 0.10)
- **Existing seeds**: Click a seed in the list, adjust **Selected Seed Tolerance**, then click **Re-run**

> Start with low tolerance (0.05–0.15) and increase gradually to avoid leaking.

---

## Remove Over-segmentation

Switch to negative seeds to remove unwanted regions:

1. Click **- Remove** (red button) or press `P` to toggle polarity
2. Click on the over-segmented area
3. The algorithm re-runs, subtracting the unwanted region

**Two removal modes** (configurable in the **Remove Logic** section):

| Mode | Use Case | Controls |
|------|----------|----------|
| **Local Cut** (default) | Remove a small localized area | **Seed Radius** slider controls erasure sphere size |
| **Competitive** (watershed) | Remove an entire neighboring structure | **Boundary Shift** slider moves the boundary (positive = subtract more) |

---

## Multi-Channel Images

For multi-channel images (e.g., RGB microscopy), the **Channel Selector** appears automatically:

- All channels are selected by default
- Uncheck noisy channels to improve segmentation
- The algorithm uses color-space distance, so structures with similar brightness but different colors can be distinguished

---

## Advanced Options

### Edge Limit

Prevents growth across strong intensity boundaries:

1. Enable the **Edge Limit** toggle
2. Adjust **Edge Threshold** (lower = stricter boundaries, default: 0.05)

### Protect Others

On by default. Prevents overwriting voxels belonging to other segments.

---

## Managing Segments

Annotate multiple structures in the same session:

- **+ New**: Create a new segment
- **Segment chips**: Click to switch between segments
- `N` / `M`: Navigate next / previous segment
- **Clear**: Delete selected segment(s) — use the list icon for multi-select mode

Each segment maintains its own seeds and tolerance settings. Switching back to a previous segment restores them.

---

## Commit Results

1. Click **Commit** to write the segmentation to the server
2. The interim overlay is cleared and the result becomes permanent

> Uncommitted changes are lost if you unlock the view.

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `P` | Toggle seed polarity (+/-) |
| `N` / `M` | Next / Previous segment |
| `G` | Grab (select) hovered segment |
| `X` | Clear current segment |
| `L` | Lock / Unlock view |
| `R` | Reset to locked view position |
| `Ctrl+Z` / `Cmd+Z` | Undo |
| `Ctrl+Shift+Z` / `Cmd+Shift+Z` | Redo |
| `Esc` | Reset all modes |

---

## Troubleshooting

- **Segmentation leaks into neighboring structures**
    - Lower the **Seed Tolerance**
    - Enable **Edge Limit**
    - For multi-channel images, deselect noisy channels

- **Segmentation does not grow enough**
    - Increase the **Seed Tolerance**
    - Place the seed on a representative part of the structure, not at the edge

- **Negative seeds not removing the right area**
    - Switch between **Local Cut** and **Competitive** modes
    - Adjust **Seed Radius** (Local Cut) or **Boundary Shift** (Competitive)

- **Algorithm runs slowly**
    - Lock a smaller region of interest

- **Changes disappeared after unlocking**
    - Always **Commit** before unlocking

- **Other issues**
    - Contact the site administrator

---
