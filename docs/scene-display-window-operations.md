---
tags: 
   - viewer
---

*Open a scene in the viewer, find its main controls, and download a region of an image.*

---

## Open the viewer

Open a dataset from `Library` (`Open Dataset`) or a scene from `Scenes` (`Open Scene`), then click `Continue`. Double-clicking a scene opens it at once. The viewer opens in its own window, called the viewer window in this guide. The portal pages stay in the main window. If nothing opens, check that your browser is not blocking pop-ups for this site. Keep the viewer window open while you use a plugin such as `Interactive Annotation`.

The viewer window has:

- A top bar with a camera icon (screenshot), a share icon, `ROI Selection`, a command-key icon that opens `Keyboard Shortcuts`, and your account menu with `Log Out`. The share icon is described in [Groups and Sharing](groups-and-sharing.md).
- A panel on the right. It shows the scene title with a Default Scene or Composed Scene badge, a `Layout` row (`XY`, `XZ`, `YZ`, `XY 3D`, `XZ 3D`, `YZ 3D`, `3D` and `4 Panel`), and two tabs, `Layers` and `Viewer`. See [Basic Image Adjustments](basic-image-adjustments.md). In a narrow window the panel starts collapsed: open it with the round button at the window's right edge.

Click in the viewer once before you use a keyboard shortcut, so that the viewer window has the focus.

---

## Select and download a region

1. Hover over one corner of the region in a view and press `B`. Move the pointer to the opposite corner and press `B` again. A box appears. Each press records the slice shown, so scroll to another slice before the second press to give the box depth, or set the Z range in the dialog. Right-click in the view to clear the box and start a new one.
2. Click `ROI Selection`, or press `Ctrl+D` (`Cmd+D` on macOS).
3. In `ROI Specifications`, choose a layer under `Select Layers` and a scale under `Select Resolution`. The ranges under `Range Specs (Pixels)` fill in from the box. Adjust them, or tick `Whole` to take a whole axis.
4. Click `Download`. The region is saved as an OME-TIFF, and some browsers ask where to save it.

A dataset with several channels downloads with all its channels. If it was converted with `Split into separate layers per channel`, select the channel layers together under `Select Layers` to get them in one file.

The dialog also has an `Annotate` button. Do not use it: the file it prepares is not listed in `Uploads` or `Library`. Annotation happens on the scene itself. See [Interactive Annotation](interactive-annotation.md).

---

## Save the scene

Press `Ctrl+S` (`Cmd+S` on macOS) in the viewer.

- For a dataset opened from `Library`, `Save as New Scene` asks for a `Scene Name`. `Save` creates the scene under `Scenes` and reopens the viewer on it. The box `Override default scene (don't create a copy)` updates the default scene instead.
- `Scene Saved` confirms a save.

Display settings, layout and view position are not saved until you save the scene, and they are lost when you open another scene in the same window. Adding or removing layers is stored at once in a saved scene.

---

## Troubleshooting

- **`Please select at least one layer and a resolution.`**: choose a layer under `Select Layers` and a scale under `Select Resolution`.
- **The ranges in `ROI Specifications` are 0**: press `B` at two corners first, then choose a layer. The ranges fill in when the layer is chosen.
- **A download stops when you leave the page**: keep the viewer window open until the progress bar completes.
- **The side panel is missing**: the window is narrow. Click the round button at the window's right edge.

---

## Next

- [Basic Image Adjustments](basic-image-adjustments.md)
- [Scenes](scenes.md)
