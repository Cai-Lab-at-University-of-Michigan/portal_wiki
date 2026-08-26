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
   viewer to place a seed. The badges show how many positive and negative seeds
   are placed.
4. Click `Run Flood Fill`.
5. Adjust and re-run until the result is right, then click `Commit`.

---

## Controlling the result

**Tolerance** decides how far the region grows. A higher value takes in voxels
that differ more from the seed. If the region spills into neighbouring
structures, lower it; if it stops short, raise it.

**Negative seeds** carve areas back out. Switch `Seed Mode` to `- Remove` and
click on the part that should not be included.

**Edge limit** stops growth at strong intensity gradients. Enable it when the
structure has a clear boundary that tolerance alone does not respect, and lower
its threshold for stricter boundaries.

`Clear` (`C`) removes every seed and lets you start again.

---

## Limits

Flood Fill runs on the CPU inside the locked region and is capped at about
16.7 million voxels (256 x 256 x 256) with a 30 second budget. Lock a smaller
region if it is refused. Unlike the AI model, it cannot read the region at a
coarser resolution, because downsampling changes the intensity gradients it
measures.

---

### Troubleshooting

- **The region grows too far**: lower the tolerance, or enable the edge limit.
- **The region does not grow**: raise the tolerance, and check the seed sits on a
  representative voxel rather than on an edge.
- **The run is refused**: the locked region is over the limit. Lock a smaller one.
- **The result vanished**: it was not committed. Click `Commit` before unlocking.
