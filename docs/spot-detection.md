---
tags: 
   - spots
   - detection
---

*Detect fluorescent spots in a converted image and add one annotation layer of points per gene to the scene.*

Whole-image spot detection needs a GPU worker. It is available only on sites configured for it. You must own the image and the open scene.

---

## Steps

1. Open the dataset or scene in the viewer (see [Library](image-library-management.md)), then click `Spot Detection` in the sidebar, under `Plugins`.
2. Under `Target scene`, choose `Image dataset`, the image to detect on and overlay. `Scene` shows the open scene. The channel table fills in once the image is chosen.
3. Under `Channel parameters`, each row is one channel of the image (`Channel`). Set the `Wavelength`, `Threshold` and `Tolerance` of each row, and remove rows you do not want with the bin icon.
4. Under `Genes (barcodes)`, click `Add gene` and tick the wavelengths whose spots must co-localize to call that gene. With no genes, the run writes point-cloud CSV files only and adds no layers.
5. Click `Start Spot Detection`. The job is listed under `Jobs`. When it finishes, reload the scene to see the points.

For a Squid acquisition, `Spot Detection (raw folder)` in the `Uploads` row menu runs detection on the raw folder.

---

## Preview on a box

Test the settings on a small region before a whole-image run.

1. Under `Preview on a box`, click `Draw a box`, then drag a rectangle on a slice in the viewer window.
2. Click `Preview`. The same detector runs on the box, and the points appear in the viewer window as temporary layers. The panel shows the number of spots per channel.
3. Adjust `Threshold` and `Tolerance`, and preview again. `Clear preview` removes the temporary points.

The temporary points are not saved with the scene. The preview does not work on a layer that has an online transform applied.

---

## Troubleshooting

- **A channel line in the preview is red and says the points were not drawn**: too many points were found. Raise `Threshold`, or draw a smaller box.
- **`Preview` is grayed out**: choose an image, draw a box, and keep the viewer window open. A red note beside the box names what is missing.
- **`Not enough permissions`**: run spot detection on an image and a scene you own.
- **`Each channel row needs a unique, positive wavelength.`**: set a different `Wavelength` above zero in every row. A channel whose name has no wavelength, for example brightfield, starts at 0.
- **The job stays `PENDING`**: it is waiting for a worker. If the site has no GPU worker for this job, it cannot run.
- **The panel says `Please open a scene to use Spot Detection`**: open a dataset or scene first.

---

## Next

- [Jobs](jobs.md)
- [3D Mean Shift](mean-shift-3d-detection.md) detects spots inside a locked region.
