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
- uncompressed `.nii` files


Files will be converted into the large-scale compatible  
[SISF format](https://github.com/Cai-Lab-at-University-of-Michigan/pySISF), optimized for efficient online visualization and annotation.

---

## Steps

1. Go to `Raw File Management`.
2. Click `Actions` next to the uploaded file.
3. Select `Convert to SISF`.
4. Confirm that the Globus upload has **fully completed** in the Globus window.  
   If confirmed, click `Yes, Continue`.
5. Enter metadata for the file:
   - Number of channels
   - Physical resolution (XYZ)
   - Image size (XYZ)
6. Click `Start Conversion`.
7. Once conversion completes, the field **SISF Conversion?** will show **Yes**.
8. *(Optional)* Click `Add to SISF Library` to add the dataset to the SISF Image Library.

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
