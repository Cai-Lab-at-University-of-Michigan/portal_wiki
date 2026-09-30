---
tags: 
   - upload
   - conversion
---

*Convert an upload into the portal's image format (SISF) so that it can be viewed and annotated.*

---

## Supported sources

- **TIFF** (`.tif`, `.tiff`): one file, or a folder of numbered slices with one file per slice. The axis order is read from the file, so save a stack with its axes stored (for example an ImageJ hyperstack or an OME-TIFF). Check `Depth (Z)` and `Number of Channels` in the form. Only the first time point is converted. A folder of signed or floating-point slices cannot be converted as CT data.
- **NIfTI** (`.nii`, `.nii.gz`). A fourth axis is read as channels.
- **Squid acquisition folders.** Upload the whole folder.

The result is stored in [SISF](https://github.com/Cai-Lab-at-University-of-Michigan/pySISF), the portal's image format.

---

## Steps

1. In `Uploads`, open the row menu of the file and choose `Convert to SISF`.
2. `Confirm Globus Upload` asks whether the transfer has finished. Click `Yes, Continue`.
3. `SISF Conversion Parameters` opens and reads the file's metadata. Check `Spatial Resolution (µm/pixel)`, `Tile Size (pixels)`, `Tile Grid (Nx, Ny, Nz)`, `Tile Overlap (%)` and `Number of Channels`. For a tiled source, also set `Scan Direction` and `Z Order`, which are not read from the file. Every field stays editable.
4. Click `Start Conversion`.
5. Follow the conversion. `Status` in `Uploads` shows `Processing...` with a percentage, and the job is listed under `Jobs`. When it ends, `Status` shows `Added` and the dataset is in `Library`. There is no separate step to add it.

`Metadata successfully extracted!` means the file was read, not that every value was found. A value the file does not state stays empty or 0 and has to be typed in. If reading failed, click `Extract Metadata` or fill the fields in by hand.

Check the voxel size before you start. If the file states no slice spacing, `Z Res` is copied from `X Res` and the form says so. That is a guess, so replace it with your real slice spacing.

Other options in the dialog:

- `Split into separate layers per channel` (multi-channel files) creates one dataset for each channel.
- Under `Register as`, `Item type` chooses `Image` or `Segmentation`. Choose `Segmentation` only to bring in an existing mask. Pick its `Parent image`: the mask must be single-channel and match the parent's size, which is checked after the conversion.
- For Squid acquisitions the dialog can also fit a flatfield correction. That is available only on sites configured for it.

---

## Data that is not `uint8` or `uint16`

A CT scan usually holds signed values (Hounsfield units). The form then shows a `Data Type Warning`, and `Start Conversion` asks `What kind of data is this?`. The storage format holds non-negative whole numbers, so the values are shifted and rounded first.

| Button | Result |
|---|---|
| `This is a CT scan (Hounsfield units)` | Values are shifted and rounded, and the shift is recorded. This is required for [MicroCT Segmentation](microct-segmentation.md). |
| `Not a CT scan, rescale to fit` | NIfTI only. Values are rescaled to fit the storage range, so absolute values are lost, and MicroCT Segmentation cannot use the result. |
| `Cancel` | Returns to the form. |

A TIFF with fractional or negative values that is not a CT scan is refused. Cancel, and convert the file to `uint16` yourself with the scaling that suits your data.

A scan whose values arrive as `uint8` or `uint16` is converted without this question, so no shift is recorded and MicroCT Segmentation cannot use it.

---

## Convert again

Choose `Already Converted (Redo?)` in the row menu, then `Yes, Redo`, and repeat the steps above.

- To correct the voxel size, the tile overlap or the channel names of a converted image, use `Edit Metadata` in `Library` instead. See [Edit Metadata](edit-metadata.md).
- A redo is refused when it would change the image's geometry (channel count, tile size or overlap, voxel size or image size), or when the dataset has revisions, the versions made with `Edit Metadata`. Delete those revisions in `Library` first. The refusal is reported as a failed job, not at the click. Read the reason under `Jobs`, `View Details`, `Result`.
- To change the tile size, tile grid or channel count of a converted image, rename the upload in `Uploads` and convert it again under the new name. Do not delete the image and convert under the same name.

---

## Troubleshooting

- **`Start Conversion` is grayed out**: a required field is empty or invalid, for example a voxel size the file does not state. Fill it in. If every field is filled in, retype one value.
- **`Status` stays at `Processing...`**: reload the page, then check `Jobs`.
- **The job shows `FAILURE`**: open `Jobs`, choose `View Details` and read `Result`. Frequent reasons:
    - `value_offset=... leaves values outside uint16 range`: a CT scan holds values outside the range the format can store after the shift. Clip or fix those values in the source.
    - `Compressed NIfTI is too large to read efficiently`: decompress the file, and upload the `.nii`.
    - `already exists with a different geometry` or `has edited versions`: see Convert again.
- **`Status` shows `Converted` instead of `Added`**: the dataset was converted but not registered. Open `Jobs`, `View Details`, and read `Result`: it ends with `auto-register skipped` and the reason. For a segmentation the reason is usually a size or channel mismatch with the parent. Then choose `Add to SISF Library` in the row menu for an image, or `Add as Segmentation` for a mask.
- **The voxel size is wrong after conversion**: use `Edit Metadata` in `Library`.

---

## Next

- [Library](image-library-management.md)
- [Jobs](jobs.md)
