---
tags: 
   - upload
   - conversion
   - globus
---

*This tutorial guides you through the file conversion process.*

---

## Supported File Formats

- Single 3D image stack (single-channel or multi-channel)
- `.tif` / `.tiff` files, assumed in **ZCYX** order  
  *(this is the typical layout exported by ImageJ)*
- `.nii` and `.nii.gz` (NIfTI). A compressed `.nii.gz` is limited to **4 GiB**;
  above that, decompress it and upload the `.nii`.
- Squid acquisition folders, read together with their `acquisition.yaml`

Files will be converted into the large-scale compatible  
[SISF format](https://github.com/Cai-Lab-at-University-of-Michigan/pySISF), optimized for efficient online visualization and annotation.

---

## Steps

1. Go to `Uploads`.
2. Click `Actions` next to the uploaded file.
3. Select `Convert to SISF`.
4. Confirm that the Globus upload has **fully completed** in the Globus window.  
   If confirmed, click `Yes, Continue`.
5. Click `Extract Metadata`. Voxel size, image size, channel count, and (for Squid
   acquisitions) the tile grid and overlap are read from the file and filled in.
   Every field stays editable, so correct anything the file states wrongly. If
   extraction fails, enter the values manually.
6. Click `Start Conversion`.
7. Once conversion completes, the field **SISF Conversion?** will show **Yes**.
8. *(Optional)* Click `Add to SISF Library` to make the dataset available under `Library`.

---

## CT data

Our storage format holds non-negative whole numbers, so a signed or floating-point
source has to be shifted and rounded before it fits. When the file is neither
`uint8` nor `uint16`, conversion asks **What kind of data is this?**

Click **This is a CT scan (Hounsfield units)**. Rounding is exact for Hounsfield
units, and the conversion records the offset it applied.

**This step is required for microCT segmentation.** The model reads absolute
Hounsfield values, so a scan converted without a recorded offset cannot be used
and the model is greyed out in the picker. See
[MicroCT Segmentation](microct-segmentation.md).

For data whose detail sits below a single whole step, such as intensities
normalised to 0-1, cancel and convert the file to `uint16` yourself, choosing the
scaling that suits the data.

---

## Progress Monitoring

- Navigate to `Jobs` to track conversion progress.
- You may cancel the job if needed.

---

### Troubleshooting

- If the job status shows `Failure`:
  - Confirm that all metadata matches the actual file.
  - View metadata under `Actions` → `View Details` on the `Jobs` page.
  - Common issues include:
    - Image size mismatch
    - Channel number mismatch

If issues persist, contact the site administrator for assistance.
