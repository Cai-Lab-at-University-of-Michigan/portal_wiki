---
tags:
   - imaging
   - chromatic-aberration
   - alignment
   - multi-channel
---

*This tutorial guides you through correcting chromatic aberration in multi-channel datasets.*

---

## Overview

Chromatic aberration occurs when different wavelengths of light focus at slightly different positions, causing color fringing or channel misalignment in fluorescence microscopy images. The Virtual Stitching tool can be used to correct these offsets by adjusting each channel independently.

---

## Understanding Chromatic Aberration

In multi-channel fluorescence imaging:
- Different emission wavelengths may have different focal planes
- Optical elements can introduce lateral (X/Y) shifts between channels
- These shifts are typically consistent across the entire field of view

Common symptoms:
- Color halos around bright features
- Misaligned structures when overlaying channels
- Offset boundaries between channels at the same location

---

## Correction Workflow

### Step 1: Open Virtual Stitching

1. Open a scene with your multi-channel dataset in the 3D viewer.
2. Navigate to **Quick Access** > **Virtual Stitching**.
3. Your current layer should be automatically selected. If not, click it in the sidebar.

### Step 2: Select Reference Channel

1. In the channel selection area, you'll see colored chips for each channel (colors match viewer display).
2. Identify your reference channel (typically the channel with the sharpest features or the one you want others aligned to).
3. **Deselect all channels** first, then keep the reference channel **unselected** — you will adjust other channels relative to it.

### Step 3: Enable Auto-Select (Recommended)

1. Enable the **Auto-select** toggle (green when active).
2. Navigate in the viewer to find a region with clear features visible in multiple channels.
3. The tile at your current position will be automatically selected.

### Step 4: Adjust Offset Channels

1. Select **one channel** that needs correction by clicking its chip (it highlights in blue).
2. Use the **X and Y sliders** to shift the channel until it aligns with the reference.
3. The viewer updates in real-time — look for:
   - Edges that should overlap
   - Point features that should coincide
   - Structures that span multiple channels

### Step 5: Apply to All Tiles

For consistent chromatic aberration across the dataset:

1. Click **Select All** in the tile grid to select all tiles.
2. Keep your single offset channel selected.
3. Adjust the X/Y offset — this applies to all tiles simultaneously.
4. Click **Save All** when satisfied.

### Step 6: Repeat for Other Channels

1. Deselect the corrected channel.
2. Select the next channel that needs correction.
3. Repeat the adjustment process.

---

## Tips for Accurate Correction

### Finding Good Reference Features

- Use bright, high-contrast features
- Structures labeled in multiple channels work best
- Fiducial markers or beads are ideal if available
- Cell boundaries or nuclei often appear in multiple channels

### Using Auto-Select

- Enable Auto-select to quickly navigate and find problem areas
- The tool automatically selects the tile at your viewer position
- Disable when you want to manually select specific tiles for comparison

### Typical Offset Ranges

- Lateral shifts (X/Y): Usually 0–20 pixels depending on objective and wavelength
- Axial shifts (Z): Can be larger, especially with high-NA objectives
- Far-red channels typically shift more than blue/green

### Multi-Tile Datasets

For tiled datasets with chromatic aberration:
1. The aberration is usually **consistent** across all tiles
2. Use Auto-select to verify alignment at a few representative tiles first
3. Select **all tiles** and **one channel** to apply the same offset globally
4. Verify at tile boundaries after applying

---

## Example Correction

For a 3-channel dataset (488nm, 561nm, 647nm) with 647nm showing lateral shift:

1. Open Virtual Stitching
2. Enable **Auto-select** and navigate to a tile with clear features
3. Deselect all channels, then select only **647nm** (the red channel chip)
4. Adjust X offset: +5 pixels, Y offset: +3 pixels
5. Verify alignment with 488nm reference channel
6. Click **Select All** tiles, then **Save All**

---

## Troubleshooting

- **Correction varies across field**: May indicate field-dependent aberration; consider correcting tiles individually
- **Z-offset not helping**: Chromatic focal shift may require re-acquisition or deconvolution
- **Changes not persisting**: Ensure you click **Save All** before closing
- **Overcorrection**: Start with small adjustments; use input fields for precise values
- **Channel colors not showing**: Channel color info comes from layer settings; ensure layer is properly configured

---

## Related

- [Virtual Stitching](virtual-stitching.md) — Full guide to the Virtual Stitching tool
