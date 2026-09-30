---
tags: 
   - metadata
   - revision
---

*Correct the voxel size, tile overlap or channel details of a converted image without converting it again.*

---

## Steps

1. In `Library`, open the row menu of the image and choose `Edit Metadata`. The entry is offered to the image's owner and to a site administrator.
2. Change what needs correcting:
    - `Spatial Resolution (µm/pixel)`: `X Res`, `Y Res` and `Z Res`.
    - `Tile Overlap (%)`: `Overlap X`, `Overlap Y` and `Overlap Z`. This applies only to images converted as several tiles.
    - `Channels`: for each channel, `Name` (required, and different for each channel), `Exposure (ms)` and `Illumination intensity`. Leave the last two blank when they are not known.
3. If the dialog says layers depend on the image and you are changing the overlap or the voxel size, tick the `I understand ... with the original image` box.
4. Click `Save`.

`Tile Size (pixels)`, `Tile Grid` and `Acquisition` are shown for reference and cannot be changed here.

---

## What saving does

- **Channel details** are saved on the image at once. Scenes created before the change keep the layer names they were made with.
- **A new voxel size or tile overlap** is saved as a new image, a revision titled `<title> r2` (then `r3`, and so on). It appears in `Library` with a `revision` badge, and `Saving a New Revision` shows the progress. The job is also listed under `Jobs`.
- The original image, its scenes and its layers stay as they were. Segmentations, point clouds and other analysis results are not copied to the revision. Shares set on the original are not copied either, so share the revision separately.
- Open the revision with `Open Dataset` in `Library`. `Set as current revision` is in the row menu of a revision, for the owner or a site administrator. It marks which version is current. It is only a label: saved scenes keep using the image they were made from.
- An image with revisions cannot be deleted, or converted again, until its revisions are deleted.

---

## Troubleshooting

- **`Edit Metadata` is not in the menu**: it is offered only to the image's owner and to a site administrator, and only for images. For an image converted with `Split into separate layers per channel`, use the parent row.
- **`Save` stays grayed out**: nothing has changed yet, or a changed value is not valid. Channel names must be filled in and different, voxel sizes above zero, overlap from zero to below 100, and exposure and intensity not negative. If layers depend on the image and you change the overlap or voxel size, also tick the acknowledgement box.
- **The dialog says the image was converted as a single tile**: there is no tile overlap to edit. The voxel size and the channels can still be changed.
- **`Request failed (400)` with `Nothing changed`**: the new values equal the stored ones after rounding.
- **`This image has no conversion record, so nothing here can be edited.`**: there is nothing to edit for that image.

---

## Next

- [Library](image-library-management.md)
- [Virtual Stitching](virtual-stitching.md) moves individual tiles by hand.
