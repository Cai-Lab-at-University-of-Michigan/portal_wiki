---
tags:
   - annotation
   - nninteractive
   - segmentation
---

*This tutorial covers the Interactive Annotation panel, where segmentation is drawn, computed, and exported.*

---

## Overview

Interactive Annotation runs inside the portal, writing to a segmentation layer in
the scene. There is nothing to download beforehand and nothing to upload back.

The panel offers a brush and eraser, `Merge` and `Split` for editing segments,
`Algorithms` for region growing and spot detection, and `AI Model` for
`nnInteractive` and the prompt-free models.

---

## Open the panel

1. Open a scene from `Library` or `Scenes`.
2. Click `Interactive Annotation` in the sidebar.

---

## Step 1: Choose a segmentation layer

Select an existing segmentation layer, or create one with `New Segmentation Layer`.

The dialog lists four downsample factors (1x, 2x, 4x, 8x) with the physical voxel
size and the maximum on-disk size each produces, and marks one `RECOMMENDED`.
Full resolution is recommended: a coarser layer is faster to create and smaller
on disk, but the detail it drops cannot be recovered afterwards. Some models
require full resolution and refuse a downsampled layer.

---

## Step 2: Lock the view

Click `Lock View`. This fixes the working region: everything the tools read and
write is bounded by it, and the tools stay disabled until it is set.

- The panel shows the locked region's size against the limit for the selected tool.
- `Reset View` returns the viewer to the locked region if you have navigated away.
- `Unlock` releases the region. Uncommitted work is confirmed before it is discarded.

The limit depends on what is selected. `nnInteractive` can read a large region at
a coarser pyramid level, so a whole scan can be locked for it. The algorithms
below read at full resolution and take a smaller region.

---

## Step 3: Annotate

### Brush and eraser

Select `Brush` (`D`) and paint on the image. `Eraser` (`E`) removes voxels.
`[` and `]` change the brush size.

### Algorithms

Select `Algorithms` and choose one. The two work differently.

**Flood Fill** grows a region from seed points by intensity similarity. Placing a
seed runs it immediately, and `Re-run` applies any parameter change made
afterwards. See [Flood Filling](flood-filling-annotation.md).

**3D Mean Shift** finds spot-like structures across the whole locked region and
takes no seeds. Its output is a set of points rather than a filled mask. Set the
parameters, then click `Run 3D Mean Shift`.

### AI Model

Select `AI Model` and pick a model from the `Model` list. Models that do not
apply to the current image cannot be selected; hover one for the reason.

**`nnInteractive`** segments from prompts you place on the image:

| Prompt | Shortcut |
|---|---|
| `Point` | `1` |
| `Scribble` | `2` |
| `Bounding Box` | `3` |
| `Lasso` | `4` |

Use `Pos` for a prompt that marks the object and `Neg` for one that marks
background, and press `P` to switch between them. Each prompt refines the mask
rather than replacing it, so start with one point and add prompts where the
result is wrong.

- `AutoRun` re-runs the model after every prompt. With it off, click
  `Run AI Segmentation`.
- `Clear Prompts` removes the prompts and leaves the mask.
- `Next Object` keeps the mask and starts a new segment.
- On a multi-channel image, `Channel` selects the channel the model sees.

For whole-volume microCT segmentation with no prompts, see
[MicroCT Segmentation](microct-segmentation.md).

---

## Step 4: Commit

Click `Commit` to write the result into the segmentation layer. Until then the
work is held as an uncommitted mask and is not part of the layer.

Use `Merge` to combine segments and `Split` to separate them. Both can be undone.

---

## Step 5: Export

With the `Algorithms` tool open, click `Export TIFF`. The segmentation layer
downloads as a TIFF named after the dataset.

---

## Keyboard shortcuts

| Key | Action |
|---|---|
| `D` | Brush |
| `E` | Eraser |
| `[` `]` | Brush size |
| `Ctrl+Z` / `Cmd+Z` | Undo |
| `Ctrl+Shift+Z` / `Cmd+Shift+Z` | Redo |
| `1` to `4` | Point, Scribble, Bounding Box, Lasso |
| `P` | Switch prompt between positive and negative |
| `T` | Toggle AutoRun |
| `S` | Run |
| `C` | Clear prompts |
| `N` / `M` | Next / previous segment |
| `G` | Grab hovered segment |
| `X` | Clear segment |
| `L` | Lock / unlock view |
| `R` | Reset view |
| `Esc` | Clear prompts and uncommitted strokes, and deselect the active tool |
| `Space` | Hold to pan |

---

### Troubleshooting

- **The tools are greyed out**: the view is not locked. Click `Lock View`.
- **`Lock View` is refused**: the region is larger than the selected tool allows.
  Zoom in, or select `nnInteractive`, which reads a large region at a coarser level.
- **The result disappeared after unlocking**: it was never committed. Click
  `Commit` before `Unlock`.
- **Nothing changed after a run**: check that the intended segmentation layer is
  selected, not the image layer.
