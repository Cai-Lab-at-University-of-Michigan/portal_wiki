---
tags:
   - imaging
   - stitching
   - alignment
   - neuroglancer
---

*This tutorial guides you through using Virtual Stitching to align multi-tile datasets.*

---

## Overview

Virtual Stitching allows you to interactively reposition individual tiles within a tiled dataset. This is useful for:
- Correcting tile alignment after acquisition
- Fine-tuning overlap regions between tiles
- Adjusting chromatic aberration offsets between channels

---

## Accessing Virtual Stitching

1. Open a scene containing a tiled image layer in the 3D viewer.
2. Navigate to **Quick Access** > **Virtual Stitching** in the sidebar.
3. The Virtual Stitching panel will open.

---

## Multi-Layer Support

You can work with multiple layers simultaneously:

1. **Ctrl+Click** (or Cmd+Click on Mac) layers in the sidebar to select multiple
2. **Shift+Click** to select a range of layers
3. A badge shows the number of selected layers
4. Tile grids from all selected layers are combined

When multiple layers share the same tile positions, selecting a grid cell selects tiles from all layers at that position.

---

## Using the Tile Grid

### Selecting Tiles

The tile grid displays all tiles arranged by their spatial positions:

- **Click** on a tile to select it (centers viewer on that tile)
- **Drag** across multiple tiles for freehand region selection
- **Ctrl+Click** (or Cmd+Click on Mac) to toggle individual tiles
- **Shift+Click** to select a rectangular range of tiles
- Click **row/column headers** to select entire rows or columns
- Use **Select All** / **Deselect All** buttons for bulk selection

### Auto-Select Mode

The **Auto-select** toggle (green when active) automatically selects the tile at your current viewer position:

- When enabled, navigating in the viewer automatically highlights the corresponding tile
- Useful for quickly finding and adjusting tiles as you browse the dataset
- Disable when you want manual tile selection to persist while navigating

### Visual Indicators

- **Blue** tiles are selected
- **Orange dot** indicates tiles with unsaved changes
- **Light blue** shows tiles in the current drag selection

---

## Adjusting Tile Positions

### Channel Selection

For multi-channel datasets, colored channel chips appear below the tile grid:

1. Each chip shows the channel name and a color swatch matching the viewer display
2. **Click** a channel chip to toggle selection (highlighted in blue when selected)
3. **Shift+Click** to select a range of channels
4. Use **Select All** / **Deselect All** for bulk channel selection

Only selected channels will be adjusted when you move the sliders.

### Position Controls

Once tiles and channels are selected, use the position controls:

- **X, Y, Z Sliders**: Drag to adjust offset in each dimension (real-time preview)
- **Input Fields**: Type exact offset values for precise positioning
- Changes are applied immediately to the viewer

The delta indicator (Δ) shows the current offset change from the original position.

---

## Saving Changes

- **Save All**: Commits all pending changes permanently
- **Discard**: Reverts all changes to original positions
- Closing the dialog without saving will also discard changes

---

## Tips

- Use **Auto-select** to quickly navigate to problem areas and select tiles
- Start with coarse adjustments using sliders, then fine-tune with input fields
- Use the viewer to verify alignment at tile boundaries
- For chromatic aberration correction, select only the channel that needs adjustment
- Changes are previewed live but not permanent until you click **Save All**

---

## Troubleshooting

- **Tiles not loading**: Ensure the layer is an IMAGE type with SISF tile metadata
- **Changes not visible**: Try refreshing the viewer or wait for cache invalidation to complete
- **Multiple channels not moving together**: Ensure all desired channels are selected (highlighted in blue)
- **Auto-select not working**: Check that Auto-select toggle is green (enabled)
- **Layers not appearing**: Click layers in the sidebar to add them to the selection
- If issues persist, contact the site administrator for assistance.
