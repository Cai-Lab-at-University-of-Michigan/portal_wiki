# {{PORTAL_NAME}} User Guide

Welcome to {{PORTAL_NAME}}.
This guide covers account setup, data upload, conversion, visualization,
annotation, and export.

---

## Quick Start

1. [Login & Account Setup](login.md)
2. [Upload Files](file-uploads.md)
3. [Convert to SISF Format](file-conversion.md)
4. [Scene Viewer](scene-display-window-operations.md)
5. [Basic Image Adjustments](basic-image-adjustments.md)
6. [Interactive Annotation](interactive-annotation.md)
7. Export the result with `Export TIFF`, described on the same page

---

## Tutorials

### Account & Access
- [Login](login.md)
- [Forgot Password](forget-password.md)
- [Groups and Sharing](groups-and-sharing.md)

### Data Preparation
- [Upload Files](file-uploads.md)
- [Convert Files to SISF Format](file-conversion.md)
- [Background Jobs](jobs.md)

### Visualization & Interaction
- [Scene Display Window Operations](scene-display-window-operations.md)
- [Basic Image Adjustments](basic-image-adjustments.md)
- [Scenes](scenes.md)
- [Image Library Management](image-library-management.md)

### Registration and Stitching
- [Virtual Stitching](virtual-stitching.md)
- [Chromatic Aberration Correction](chromatic-aberration-correction.md)

### Annotation
- [Interactive Annotation](interactive-annotation.md) - brush, algorithms, and nnInteractive
- [Flood Filling](flood-filling-annotation.md)
- [MicroCT Segmentation](microct-segmentation.md)

---

## Troubleshooting / FAQs

- **Upload not visible?** Check the Globus transfer status, and check whether you
  are looking at the personal or the group context.
- **Black image?** Adjust brightness, or check that conversion finished.
- **Annotation tools greyed out?** The view is not locked. See
  [Interactive Annotation](interactive-annotation.md).
- **`Virtual Desktop` in the sidebar does not open.** It is not in service.
  Annotation runs in the browser.
- **`Annotate` in the ROI dialog.** Use `Download` for a local copy of a region.
  To annotate, open `Interactive Annotation` on the scene instead.

If problems persist, contact the site administrator.

---

## About

This portal supports:

- Large-scale multimodal microscopy data
- Cloud-enabled storage and streaming
- Neuroglancer-based visualization
- Interactive and AI-assisted annotation, including nnInteractive

Some tools are available only on sites configured for them, including
`Spot Detection`, `Online Transform`, and `MouseJoint (microCT)`.
