---
tags:
   - annotation
   - nninteractive
   - segmentation
---

*This tutorial covers the Interactive Annotation panel, where segmentation is drawn, computed, and exported.*

---

## Overview

Interactive Annotation runs inside the portal. Segmentation is written directly
to a layer in the scene, so nothing has to be downloaded first and nothing has to
be uploaded back.

The panel combines four kinds of tool:

- manual **brush** and **eraser**
- **Merge** and **Split** for editing existing segments
- **Algorithms** that compute a region from seed points
- **AI Model**, including `nnInteractive`

---

## Open the panel

1. Open a scene from `Library` or `Scenes`.
2. Click `Interactive Annotation` in the sidebar.

---

## Step 1: Choose a segmentation layer

Select an existing segmentation layer, or create one with `New Segmentation Layer`.

The dialog lists four downsample factors (1x, 2x, 4x, 8x) with the physical voxel
size and the maximum on-disk size each produces, and marks one `RECOMMENDED`.

**Full resolution is the recommended choice.** Whoever opens this dialog is about
to annotate, and detail is what they came for: a layer created at a quarter or an
eighth of the image's resolution loses that detail before the first stroke, and it
cannot be recovered afterwards. The cost of full resolution is disk and time,
which is why the other options remain, and why the figure matters on a large
image: a full-resolution segmentation layer beside a 400 GB image is itself
400 GB. Some models also require it. `MouseJoint (microCT)` produces a
full-resolution mask and refuses a downsampled layer outright.

---

## Step 2: Lock the view

Click `Lock View`. This fixes the working region: everything the tools read and
write is bounded by it, and the tools stay disabled until it is set.

- The panel shows the locked region's size against the limit for the selected tool.
- `Reset View` returns the viewer to the locked region if you have navigated away.
- `Unlock` releases the region. Uncommitted work is confirmed before it is discarded.

Large regions are handled by reading a coarser pyramid level rather than by
refusing the region, so a whole scan can be locked for the AI model.

---

## Step 3: Annotate

### Brush and eraser

Select `Brush` (`D`) and paint on the image. `Eraser` (`E`) removes voxels.
Undo and redo apply to the current segment.

### Algorithms

Select `Algorithms` and choose one. The two have different controls.

**Flood Fill** grows a region from seed points by intensity similarity. Placing a
seed runs it immediately, and `Re-run` applies any parameter change made
afterwards. Its controls are named for what they act on, such as
`New Seed Tolerance` and `Selected Seed Tolerance`. See
[Flood Filling](flood-filling-annotation.md).

**3D Mean Shift** detects spot-like structures in the locked region. Its
parameters are listed under their internal names (`bandwidth`,
`intensity_threshold`, `bg_sub_threshold`, `merge_distance`). Set them, then
click `Run 3D Mean Shift`.

### AI Model

Select `AI Model` and pick a model from the `Model` list.

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

`SAM2`, `MedSAM2`, and `SAM3` appear in the list but are not implemented, and
stay greyed out.

For whole-volume microCT segmentation with no prompts, see
[MicroCT Segmentation](microct-segmentation.md). That model is available on the
RE-JOIN portal only.

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
| `P` | Switch prompt between positive and negative |
| `1` - `4` | Point, Scribble, Bounding Box, Lasso |
| `T` | Toggle AutoRun |
| `S` | Run |
| `C` | Clear prompts |
| `G` | Grab hovered segment |
| `X` | Clear segment |
| `L` | Lock / Unlock view |
| `R` | Reset view |
| `Esc` | Reset |
| `Space` | Hold to pan |

---

### Troubleshooting

- **The tools are greyed out**: the view is not locked. Click `Lock View`.
- **`Lock View` is refused**: the region is larger than the selected tool allows.
  Zoom in, or switch to the AI model, which reads large regions at a coarser level.
- **The model is greyed out in the list**: it is either not implemented, or not
  applicable to this image. Hover it for the reason.
- **The result disappeared after unlocking**: it was never committed. Click
  `Commit` before `Unlock`.
- **Nothing changed after a run**: check that the intended segmentation layer is
  selected, not the image layer.
