---
tags:
   - napari
   - annotation
   - flood-filling
   - watershed
---

*This tutorial guides the process for using the Neuron Annotator plugin for 3D/4D neuron segmentation in Napari.*

---

## First-time Usage

**Neuron Annotator** is a Napari plugin for interactive segmentation using flood filling and watershed algorithms.

1. Open Napari and load your image
2. If nnInteractive plugin is opened, close it.
3. Go to **Plugins → Neuron Annotator** 

---

## Prepare Image Data (Optional)

### For 4D Multichannel Data

1. The plugin displays **channel selection** checkboxes (Red, Green, Blue)
2. Select which channels to mix for each color
3. Click **"Synthesize RGB"**

### Auto Contrast Enhancement

- Enable **"Enhance (Auto Contrast)"** to improve visualization
- Adjust percentile range (default: 1% - 99.9%) if needed

---

## Annotate

### Step 1: Add Seeds

1. Ensure `Add (+)` mode is selected
2. Click on the structure you want to segment
3. The algorithm automatically grows the region based on intensity similarity

### Step 2: Adjust Tolerance

- Use the **"Seed Tolerance"** slider to control growth aggressiveness
- Tolerance limits are automatically scaled based on the number of channels
- For per-seed adjustment: modify the slider and click **"Apply to Selected"**

### Step 3: Remove Overflow

If segmentation grows too much:

1. Switch to `Remove (-)` mode
2. Click on the over-segmented area
3. Use **Local Cut** (recommended) — erases a spherical region based on the "Radius" slider

### Step 4: Manage Multiple Segments

- Click **"New"** to create a new segment
- Use **"Prev"** and **"Next"** to navigate between segments
- Each segment gets a unique color

**Segment Operations:**

- **Undo/Redo** — Remove or restore the last seed point
- **Reset** — Clear all seeds from current segment
- **Delete** — Remove entire segment (unless it is the last segment)
- **Merge** — Multi-select segments with **Ctrl+Click**, then click **"Merge"**
- **Freeze** — Lock the current segmentation to prevent further changes
- **Restart** — Reload the image and clear all segments

---

## Advanced Features

### Edge Constraints

Prevents segmentation from growing across strong intensity gradients.

1. Enable **"Edge Limit"** checkbox
2. Adjust **"Edge Threshold"** slider (lower = stricter boundaries)
3. Click **"Preview Edges"** to visualize detected edges

> **Note**: This feature may not work perfectly in all cases.

---

## Save Your Work

### Export Segmentation

1. Click **"Export"**
2. Choose filename (e.g., `result.nii.gz`)
3. Creates a NIfTI file with all segments labeled

### Fine-Tuning (Optional)

Use Napari's built-in **brush/eraser tools** on the labels layer for manual corrections.

> **Note**: Save/Load Project has known bugs and is not recommended.

---

## Troubleshooting

- **Segmentation grows too aggressively**
    - Lower the **Seed Tolerance** value
    - Enable **Edge Limit** for boundary constraints

- **Segmentation does not grow enough**
    - Increase the **Seed Tolerance** value
    - Check that your seed point is placed on a representative pixel

- **Local Cut removes too much or too little**
    - Adjust the **Radius** slider before clicking

- **4D data not displaying correctly**
    - Use **"Synthesize RGB"** to create a visualization
    - Verify channel selection checkboxes are configured

- **Export fails**
    - Ensure you have write permissions to the destination folder
    - Check that at least one segment exists

- **Plugin not appearing in menu**
    - Confirm the plugin is installed
    - Restart Napari

- **Other issues**
    - Contact the site administrator

---
