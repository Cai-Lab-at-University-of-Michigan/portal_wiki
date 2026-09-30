---
tags:
   - annotation
   - flood-filling
   - segmentation
---

*Segment a structure by growing a region from seed points.*

---

## Steps

1. Open `Interactive Annotation` in the sidebar and select the segmentation layer in the viewer window, as described in [Interactive Annotation](interactive-annotation.md).
2. In the panel, choose `Algorithms`, then `Flood Fill`.
3. Click `Lock View`.
4. Under `Seed Mode`, choose `+ Add` and click on the structure in the viewer. The region grows as soon as the seed is placed, so you do not start a run yourself.
5. Adjust the result, as described below.
6. Click `Commit` to write the result into the segmentation layer.

The result goes to the segment selected under `Segmentation`. A new run replaces that segment's uncommitted result.

---

## Adjust the result

Changes to `Edge Limit`, `Edge Threshold`, `Channels` and `Protect Others` apply to the next seed you place, or when you click `Re-run`. They do not change the region on their own.

- `New Seed Tolerance` sets how far a connected voxel may differ from the seed voxel and still join the region, as a fraction of the typical intensity range in the locked region (extreme values are ignored). A lower value gives a tighter region. It applies to the next seed you place. On a multi-channel image the difference is measured across the selected channels.
- To change a seed that is already placed, click it in `Per-Seed Parameters`, change `Selected Seed Tolerance`, and click `Re-run`.
- `Edge Limit` removes voxels at strong intensity edges from the region. When it is on, `Edge Threshold` appears. A lower value removes more.
- On a multi-channel image, tick the channels to use under `Channels`. At least one must stay selected.
- `Protect Others` keeps the uncommitted voxels of other segments from being overwritten by this run. Segments already committed are protected when you click `Commit`, by `Don't overwrite existing segments`.

To carve an area out of the region, choose `- Remove` under `Seed Mode` and click the part that should not be included. `Remove Logic` decides how:

- `Competitive` lets the negative seed compete with the positive one for the boundary between them. `Boundary Shift` moves that boundary.
- `Local Cut` removes the region inside a sphere around the seed. A separate branch of the region that continues beyond the sphere is kept. The radius is set by `New Seed Radius` or `Selected Seed Radius`.

`Remove Logic` applies to the removal seeds you place after choosing it. A placed removal seed keeps its logic, shown as `C` for `Competitive` and `LC` for `Local Cut` in the seed list.

`Undo` (`U`) and `Clear` (`C`), next to the seed counts under `Seed Mode`, change the seeds only. `Undo` removes the last seed and `Clear` removes every seed. The region is refreshed by `Re-run` or a new seed. The other `Undo` and `Clear` in the panel act on the uncommitted mask and on the selected segment. The current result stays in the uncommitted mask until you undo it with `Ctrl+Z` (`Cmd+Z` on macOS), or until you commit.

---

## Troubleshooting

- **The region grows too far**: lower `New Seed Tolerance` for the next seed, or lower `Selected Seed Tolerance` and click `Re-run` for a seed already placed. Switching on `Edge Limit` and clicking `Re-run` also helps.
- **The region does not grow**: raise the tolerance, and check that the seed sits on a typical voxel of the structure, not on an edge.
- **A setting change did nothing**: for a seed already placed, click `Re-run`.
- **`Image region too large for Flood Fill`**: click `Unlock`, zoom in or lower the Z value, then click `Lock View` again.
- **`Lock View` is grayed out**: see [Interactive Annotation](interactive-annotation.md).

---

## Next

- [Interactive Annotation](interactive-annotation.md) covers segments, `Commit` and `Export TIFF`.
