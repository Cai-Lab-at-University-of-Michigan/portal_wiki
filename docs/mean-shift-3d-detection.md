---
tags:
   - annotation
   - mean-shift
   - spot-detection
---

*Detect bright spots, such as puncta, inside a locked region and save them as points.*

3D Mean Shift needs no seeds. It writes points to an annotation layer, so there is nothing to commit. On a multi-channel image, detection runs on the brightest value across all channels.

---

## Steps

1. Open `Interactive Annotation` in the sidebar. In the viewer window, open the `Layers` tab, click the image layer, and open its `Info` tab. Under `Annotation Layer`, click `New`, or `Load` to use an existing one. Then click the annotation layer in the layer list to select it.
2. In the panel, choose `Algorithms`, then `3D Mean Shift`.
3. Click `Lock View`. `Region` shows the locked region.
4. Set the parameters.
5. Click `Run 3D Mean Shift`. A message reports `Detected N points`, and the points appear in the viewer.
6. To keep the points outside the portal, click `CSV`. The file lists the point coordinates.

A run that finds points replaces the points of the annotation layer. If it finds none, the layer keeps its previous points even though the message reads `Detected 0 points`. With any layer other than an annotation layer selected, for example the image layer you used in step 1, the panel says `Select an annotation layer to run this algorithm`.

---

## Parameters

The panel labels each parameter with its internal name.

| Parameter | What it sets |
|---|---|
| `bandwidth` | Width of the smoothing kernel around each spot. Larger values pull nearby peaks together. |
| `intensity_threshold` | Minimum raw voxel intensity considered. It is in the image's own intensity units. |
| `bg_sub_threshold` | Minimum background-subtracted intensity. |
| `merge_distance` | Peaks closer than this distance are merged into one. |
| `min_component_size` | Minimum size of a connected component used as a starting point. |
| `anisotropy_z` | Z voxel size relative to XY. Raise it when the Z spacing is coarser. |
| `snr_threshold` | Minimum local signal-to-noise ratio for post-filtering. 0 turns the filter off. |
| `boundary_margin` | Spots closer than this many voxels to the edge of the region must pass a stricter signal-to-noise test. No effect when `snr_threshold` is 0. |
| `adaptive_bw` | Scales the bandwidth of each spot by its local signal-to-noise ratio. An on/off setting shown as a number box: enter 1 for on and 0 for off. |

---

## Troubleshooting

- **Too many false spots**: raise `intensity_threshold`, `snr_threshold` or `bg_sub_threshold`. Set `intensity_threshold` above the background level of your image.
- **Real spots are missed**: lower `intensity_threshold` and `bg_sub_threshold`, or lower `snr_threshold`. Lower `bandwidth` if nearby spots are merged.
- **One spot gets several points**: raise `merge_distance`.
- **Spots in neighboring slices are merged, or one spot is split across slices**: set `anisotropy_z` to the ratio of the Z spacing to the XY spacing.
- **The image is bright almost everywhere**: the run keeps only the brightest voxels and a limited number of starting points, and a long run can return partial results, so spots can be missed. Raise `intensity_threshold` or `bg_sub_threshold`, or lock a smaller region.
- **`Image region too large for 3D Mean Shift`**: lock a smaller region. Zoom in or lower the Z value.
- **`Run 3D Mean Shift` is grayed out**: select an annotation layer, choose the tool, and lock the view.

---

## Next

- [Interactive Annotation](interactive-annotation.md)
- [Spot Detection](spot-detection.md) runs on a whole image.
