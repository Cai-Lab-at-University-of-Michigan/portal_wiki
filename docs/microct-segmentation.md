---
tags:
   - annotation
   - microct
   - segmentation
---

*Segment a whole microCT scan with a model that takes no prompts.*

The microCT model is available only on sites configured for it. It needs a GPU worker.

---

## Before you start

The microCT model segments the whole volume, so there is no region to select and no view to lock. A run is queued as a background job.

Check these before you run the model:

- **The scan was converted as CT data.** During conversion, answer `What kind of data is this?` with `This is a CT scan (Hounsfield units)`. See [Convert to SISF](file-conversion.md). A scan converted any other way does not offer the model.
- **The recorded voxel size is correct for the scan.** If it is not, correct it with `Edit Metadata`. See [Edit Metadata](edit-metadata.md).
- **You own the image and the segmentation layer.** A dataset shared with you cannot be used with this model.
- **The segmentation layer is at full resolution.** In `New Segmentation Layer`, pick the full-resolution option, marked `RECOMMENDED` and `(full resolution)`. The model writes a full-resolution mask.
- **The segmentation layer belongs to this image.** Create it from the image you are segmenting.
- **No online transform is applied** to the image. Very large images are also refused.

---

## Steps

1. Open the dataset, then click `Interactive Annotation` in the sidebar.
2. Create a segmentation layer at full resolution and select it, not the image layer. See [Interactive Annotation](interactive-annotation.md).
3. Under `Segmentation`, select the segment that should receive the result.
4. Choose the `AI Model` tool, then choose the microCT model in the model list.
5. Click `Run Model`.

A progress dialog opens, and the run also appears under `Jobs`. You can close the dialog and leave the page. The mask appears in the viewer when the run finishes. A second run cannot be queued on the same scene while one is in progress.

The run replaces the selected segment with the model result, including voxels inside the mask that currently belong to other segments. Voxels the model does not mark keep their segment. `Don't overwrite existing segments` does not apply to this model.

---

## After the run

The mask is already written into the segmentation layer, so there is no `Commit` for this model. Review it in the viewer. To correct it, choose `Brush` or `Eraser`, click `Lock View`, edit, and `Commit`.

`Export TIFF` downloads the whole layer at full resolution and is not suited to a whole-joint layer. See the warning in [Interactive Annotation](interactive-annotation.md).

---

## Troubleshooting

- **The microCT model is not in the model list**: select the segmentation layer you created from the image, not the image layer. Check that the scan was converted as CT data. Convert the file again with `This is a CT scan (Hounsfield units)` if it was not.
- **`The segmentation layer is downsampled ...`**: create a new segmentation layer at full resolution and run again.
- **`That segmentation layer does not belong to this image`**: create the layer from this image.
- **The job fails**: open `Jobs`, choose `View Details`, and read `Result`. A message about the voxel size means the resolution recorded for the scan is wrong. Correct it in `Edit Metadata`, then run again.

---

## Next

- [Interactive Annotation](interactive-annotation.md)
- [Convert to SISF](file-conversion.md)
