---
tags: 
   - motion
   - alignment
---

*Align the Z slices of a converted image so that the tissue stays in place.*

Motion Correction treats the Z slices of the image as the frames of a recording. Each slice is aligned to the one before it, and the result is written as a new dataset. The original stays as it was.

---

## Steps

1. Open the dataset or scene in the viewer (see [Library](image-library-management.md)), then click `Motion Correction` in the sidebar, under `Plugins`.
2. Under `Input`, choose the `Layer` to correct, then choose the `Channels` that show the tissue. Every channel is moved by the same estimate.
3. Under `Advanced`, leave `Max shift per slice (px)` empty (`Automatic`). Lower it only if the `Result` card says the estimated motion is too large.
4. Keep `Add the corrected image to the open scene` ticked to get the result as a new layer. To add it you must own the scene. Otherwise untick the box.
5. Click `Run motion correction`. A progress dialog opens, and the job is listed under `Jobs`. You can close the dialog and keep working.
6. When the run finishes, the `Result` card shows the numbers. Click `Reload scene` to show the new layer, or `Open corrected dataset` to open the result on its own.

The result is a new dataset in `Library`, titled `<title> (motion corrected)`. A repeat run is numbered, for example `(motion corrected #2)`. It is private to the person who ran it. Use `Share Dataset` to share it.

The `Result` card lists `Slices`, `Original size`, `Corrected canvas`, `Total shift`, `Largest step between two slices` and `Mean confidence`. `Mean confidence` is informational and is often low on noisy endoscopy recordings, so judge the corrected image by eye.

---

## Troubleshooting

- **`Could not start motion correction`**: the message names the cause. You need editor access to the image, the image must be converted, and it needs more than one Z slice.
- **`A motion correction of '<title>' is already ...`**: a run is pending or started. Wait for it to finish, or cancel it on the `Jobs` page.
- **The job stays `PENDING`**: it is waiting for a free worker, for example behind a stitching job. If it never starts, contact the site administrator.
- **`Motion correction failed`**: read the message in the `Result` card or under `Jobs`, `View Details`, `Result`. It names the cause, for example that the estimated motion is too large (check for blank or featureless slices, or lower `Max shift per slice (px)`) or that the image is larger than the job accepts.
- **The recording is not in Z**: the frames must already be the Z axis of the file. Save the recording as a TIFF whose frame axis is Z, upload it again, and convert it. See [Convert to SISF](file-conversion.md).

---

## Next

- [Library](image-library-management.md)
- [Jobs](jobs.md)
