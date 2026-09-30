---
tags: 
   - registration
   - alignment
---

*Align one layer of a scene onto another, or move, scale and rotate a layer by hand.*

Online Transform changes how a layer is displayed in the scene. It does not change the stored image.

---

## Steps

1. Open the dataset or scene in the viewer (see [Library](image-library-management.md)), then click `Online Transform` in the sidebar, under `Plugins`. Both layers must be in one scene. Use `Compose Scene` in [Scenes](scenes.md) to put them there.
2. In the viewer window, select the layer to move. The panel names it as the `Transform target`.
3. Under `Auto-Align`, choose the `Fixed` layer that the target should match. Both must be different image layers with the same voxel size, and you must own both layers and the scene.
4. For multi-channel layers, pick `Fixed channel` and `Moving channel` so that the same stain is compared on both layers.
5. If an `Engine` choice is offered, pick one.
6. Click `Compute alignment`. The estimate is applied at once, and a badge such as `conf 0.14` shows the confidence. Review the overlay in the viewer, then fine-tune the result. `Reset` beside `Compute alignment` returns to the computed estimate.

To align a band of slices instead of the whole volumes, switch on `Match a Z range`. Enter the `Fixed slice` and the `Moving slice`, or click `Use current` to take the slice the viewer shows, and set `Thickness`. `Match a Z range` is available only with some engines. If the chosen engine does not support it, the panel says so. The whole layer still moves, not just the band.

---

## Adjust by hand

- `Translate (voxels)`, `Scale`, `Rotate (°)`, `Shear` and `Reflect` change the target directly.
- `Reset` in `Transform Controls` removes the transform, so the target returns to its original position.
- `Save` under `Snapshots` keeps the current transform for this session. Click `Snapshot 1`, `Snapshot 2`, and so on to return to one. Snapshots are lost when you leave the panel.

---

## Save or load a matrix

- `Transform matrix` shows the 4 x 4 matrix of the target. `Download` saves it as a text file whose header states its conventions.
- `Load affine matrix` reads a matrix from a file. Click `Choose file…`, and set `Axis order`, `Units`, `Direction` and `Rotation centre` to match how the matrix was made. A file written by `Download` sets them itself.

---

## Troubleshooting

- **`Compute alignment` is grayed out**: choose a `Fixed` layer, and select the layer to move in the viewer window.
- **A message appears under `Compute alignment`**: read it. It names the cause, for example that you do not own a layer, that their voxel sizes differ, or that the image is too large to align whole.
- **`Match a Z range` is refused**: choose an engine that supports it.
- **The panel says `Please open a scene to use Online Transform`**: open a dataset or scene first, and keep the viewer window open.

`Auto-align` in [Virtual Stitching](virtual-stitching.md) is a different tool. It corrects the tiles inside one tiled image, while `Auto-Align` here registers two layers.

---

## Next

- [Scene Viewer](scene-display-window-operations.md)
