# User Guide

This guide takes you from a new account to an exported segmentation: account setup, upload, conversion, viewing, annotation and export.

---

## Quick Start

1. [Sign up and log in](login.md). A site administrator must activate a new account and assign your upload collection.
2. [Upload files](file-uploads.md) with Globus, then click `Scan & Refresh` in `Uploads`.
3. [Convert the file to SISF](file-conversion.md). The finished dataset appears in `Library`.
4. [Open the dataset](image-library-management.md) in the viewer with `Open Dataset`.
5. [Annotate](interactive-annotation.md): click `Interactive Annotation` in the sidebar, create a segmentation layer, annotate, then `Commit` the result.
6. [Export](interactive-annotation.md#export) the segmentation: choose `Algorithms`, then `Export TIFF`.

---

## Tutorials

### Getting Started
- [Login](login.md)
- [Forgot Password](forget-password.md)
- [Navigation and Settings](navigation.md)
- [Groups and Sharing](groups-and-sharing.md)

### Data
- [Uploads](file-uploads.md)
- [Convert to SISF](file-conversion.md)
- [Jobs](jobs.md)
- [Library](image-library-management.md)
- [Edit Metadata](edit-metadata.md)

### Visualization
- [Scene Viewer](scene-display-window-operations.md)
- [Basic Image Adjustments](basic-image-adjustments.md)
- [Scenes](scenes.md)

### Registration and Stitching
- [Virtual Stitching](virtual-stitching.md)
- [Chromatic Aberration Correction](chromatic-aberration-correction.md)
- [Online Transform](online-transform.md)
- [Motion Correction](motion-correction.md)

### Annotation
- [Interactive Annotation](interactive-annotation.md)
- [Flood Filling](flood-filling-annotation.md)
- [3D Mean Shift](mean-shift-3d-detection.md)
- [MicroCT Segmentation](microct-segmentation.md)
- [Spot Detection](spot-detection.md)

---

## Troubleshooting / FAQs

- **Upload not visible?** Click `Scan & Refresh` in `Uploads`. See [Uploads](file-uploads.md).
- **`Inactive user` when you log in?** Your account is waiting to be activated by the site administrator. `Continue with Google` shows a message that the account is not active yet. The fix is the same.
- **The viewer does not open?** Check that your browser is not blocking pop-ups for this site.
- **Black image?** See [Basic Image Adjustments](basic-image-adjustments.md).
- **A tool or `Lock View` grayed out?** Hover over a grayed tool for the reason. `Lock View` becomes available once a tool is chosen. See [Interactive Annotation](interactive-annotation.md).
- **Where do I annotate?** Open the dataset, then click `Interactive Annotation` in the sidebar. The `ROI Specifications` dialog in the viewer has a `Download` button for a local copy of a region, and an `Annotate` button that is not part of this workflow.

If problems persist, contact the site administrator.
