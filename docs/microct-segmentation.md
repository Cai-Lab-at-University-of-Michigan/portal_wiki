---
tags:
   - annotation
   - microct
   - segmentation
---

*This tutorial covers whole-volume segmentation of mouse joint microCT scans.*

> Available on the RE-JOIN portal only.

---

## Overview

`MouseJoint (microCT)` is an nnU-Net model for mouse femur-tibia joint
segmentation. It takes no prompts and segments the whole volume, so there is no
region to select and no view to lock. A run is queued as a background job and
takes several minutes.

---

## Before you start

Three conditions have to be met, and each is refused with a message naming the cause.

**1. The scan was converted as CT data.**  
The model reads absolute Hounsfield values, so the conversion must have recorded
the intensity offset it applied. During conversion, answer
**What kind of data is this?** with **This is a CT scan (Hounsfield units)**.
See [Convert Files to SISF Format](file-conversion.md).

A scan converted without this is refused, and the model stays greyed out in the
model list.

**2. The segmentation layer is at full resolution.**  
The model produces a full-resolution mask, so the destination layer has to be on
the image's own grid. In `New Segmentation Layer`, pick the option marked
`(full resolution)`. On a large scan this is not always the pre-selected option.

**3. The segmentation layer belongs to this image.**  
Create it from the image you are segmenting. A layer created from a different
image is drawn with that image's transform and would not line up.

The model also declines images above 2,000,000,000 voxels, and images with an
online transform applied.

---

## Run the model

1. Open the scene and click `Interactive Annotation` in the sidebar.
2. Select the segmentation layer.
3. Select the `AI Model` tool.
4. Choose `MouseJoint (microCT)` from the `Model` list.
5. Click `Run Model`.

The panel opens a progress dialog, and the run also appears under `Jobs`. You can
close the dialog and leave the page. A second run cannot be queued on the same
scene while one is in progress.

---

## After the run

The mask is written into the segmentation layer. Review it in the viewer, correct
it with the brush and eraser, and export it with `Export TIFF`. See
[Interactive Annotation](interactive-annotation.md).

---

### Troubleshooting

- **`MouseJoint (microCT)` is greyed out**: hover it for the reason. The usual
  cause is a scan converted without its intensity scale recorded.
- **"The segmentation layer is downsampled ..."**: create a new segmentation
  layer at full resolution and run again.
- **"That segmentation layer does not belong to this image"**: create the layer
  from this image.
- **The job fails**: open `Jobs`, then `Actions` → `View Details` for the error.
