---
tags: 
   - viewer
---

*This tutorial demonstrates basic operations for the Scene Viewer.*

---

## Basic Operations

1. **ROI Selection**  
   Hold `Ctrl+B` (Windows/Linux) or `Cmd+B` (macOS), then drag your mouse to select a region of interest (ROI).

2. **Download an ROI**  
   After selecting an ROI, click `ROI Selection` or press `Ctrl+D` / `Cmd+D`.  
   Choose the layers and the resolution, then click `Download`. The file streams
   to your browser as a TIFF, with progress shown in the dialog. Several layers
   can be downloaded at once.

3. **Share the Scene**  
   Click `Share` icon, then copy the generated link and share it with collaborators.

4. **Save the Scene**  
   To save the current scene (view, layers, settings), press `Ctrl+S` (Windows/Linux) or `Cmd+S` (macOS) in the viewer window.  
   This saves your current visualization state for later reuse or sharing.

---

## Annotating a region

Annotation runs inside the portal, on the scene itself. You do not need to
download an ROI first. Open `Interactive Annotation` from the sidebar and lock
the region you want to work on. See
[Interactive Annotation](interactive-annotation.md).

---

### Troubleshooting

- **The `Download` button does nothing**: check that a layer and a resolution are
  both selected.
- **Leaving the page cancels a download**: keep the tab open until the progress
  bar completes.
