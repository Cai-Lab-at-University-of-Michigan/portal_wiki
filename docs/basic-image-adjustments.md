---
tags: 
   - image
---

*This tutorial demonstrates basic image adjustments.*

---

## Basic Image Adjustments

1. Open an image or scene. The adjustments panel appears on the right side of the
   page and controls visualization settings in the Neuroglancer viewer.
2. Adjust the layout as needed.
3. Select an image layer to make layer-specific adjustments, such as:
   - Brightness
   - Contrast
   - Channel color
4. To save the current visualization settings, press `Ctrl+S` (Windows/Linux) or
   `Cmd+S` (macOS) in the Scene Display Window.

---

## 3D volume rendering

The `Volume Rendering` block offers four modes:

| Mode | What it shows |
|---|---|
| `Off` | No 3D volume rendering |
| `On` | Samples blended along each ray, weighted by opacity |
| `Max` | The brightest sample along each ray |
| `Min` | The dimmest sample along each ray |

`Max` is a maximum intensity projection and is the usual choice for CT data.

`Gain` applies in `On` mode only. It is exponential: the number shown is followed
by the multiplier it produces, so 0 means x1.

`Resolution` controls how many samples are taken along each ray. Higher values
look better and render more slowly. It applies in every mode except `Off`.

The block appears both above the layer tabs, where it applies to the scene, and
under a selected image layer, where it applies to that layer.

---

### Troubleshooting

- **The image is black**: raise the brightness, or check that the layer is visible.
- **`Gain` does nothing**: it applies in `On` mode only.
