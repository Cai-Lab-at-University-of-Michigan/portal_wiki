---
tags:
   - annotation
   - flood-filling
   - segmentation
---

*This tutorial covers the Flood Fill algorithm in the Interactive Annotation panel.*

---

## Overview

Flood Fill grows a region outward from seed points, taking in neighbouring voxels
whose intensity is close enough to the seed. It suits structures that are
continuous and distinct from their surroundings, and it runs on the region you
have locked.

It runs in the portal. Set up the panel first, as described in
[Interactive Annotation](interactive-annotation.md).

---

## Steps

1. Select the segmentation layer and click `Lock View`.
2. Select the `Algorithms` tool, then `Flood Fill`.
3. Under `Seed Mode`, keep `+ Add` selected and click on the structure in the
   viewer. **The region grows as soon as the seed is placed.** There is no
   separate button to start it.
4. Adjust the parameters below, then click `Re-run` to apply them.
5. Repeat until the result is right, then click `Commit`.

Each new seed runs on its own with the values currently set under
`New Seed Tolerance` and `New Seed Radius`. Editing the parameters of a seed
already placed stages the change, and `Re-run` applies it.

---

## Controlling the result

**`New Seed Tolerance`** sets how far the *next* seed will grow. A higher value
takes in voxels that differ more from the seed.

**`Selected Seed Tolerance`** changes the seed already selected. The change is
staged until `Re-run`.

**Negative seeds** carve areas back out. Switch `Seed Mode` to `- Remove` and
click on the part that should not be included. `Remove Logic` decides how:

- `Competitive` lets the negative seed compete with the positive one for the
  boundary between them, adjusted by `Boundary Shift`.
- `Local Cut` erases a sphere around the seed, sized by `New Seed Radius` or
  `Selected Seed Radius`.

**`Edge Limit`** stops growth at strong intensity gradients. Enable it when the
structure has a clear boundary that tolerance alone does not respect, and lower
`Edge Threshold` for stricter boundaries.

`Clear` (`C`) removes every seed and lets you start again.

---

## Limits

Flood Fill runs on the CPU inside the locked region, and the region has to be
small enough for it: the panel shows the locked size against the limit. Lock a
smaller region if a run is refused. Unlike `nnInteractive`, it cannot read the
region at a coarser resolution, because downsampling changes the intensity
gradients it measures.

---

### Troubleshooting

- **The region grows too far**: lower `New Seed Tolerance` for the next seed, or
  lower `Selected Seed Tolerance` and click `Re-run` for one already placed.
  Enabling `Edge Limit` also helps.
- **The region does not grow**: raise the tolerance, and check the seed sits on a
  representative voxel rather than on an edge.
- **A parameter change did nothing**: parameters for a seed already placed are
  staged. Click `Re-run`.
- **The run is refused**: the locked region is over the limit. Lock a smaller one.
