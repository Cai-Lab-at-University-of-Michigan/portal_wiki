---
tags: 
   - image
---

*Change how the layers of a scene are displayed: contrast, intensity range and 3D rendering.*

---

## Steps

1. Open a scene in the viewer. The panel on the right has two tabs, `Layers` and `Viewer`.
2. Under `Layout`, choose a view. 3D rendering needs a layout with a 3D panel, such as `3D` or `4 Panel`.
3. In `Layers`, click an image layer, then open its `Settings` tab.
4. Under `Channels`, click a channel to open its controls:
    - `Contrast` changes the contrast of the channel.
    - `Intensity Adjustment` sets the range of values shown. Type values under `Range`, or use the presets `Min-Max`, `1-99%` and `5-95%`. `Auto` picks a range from the image, and you can click it again to tighten the range further. `Reset` restores the full range. `View` only changes the span shown in the histogram.
5. `Blending` (`Default` or `Additive`) and `Opacity` in the same tab change how the layer combines with the others.
6. Save the scene to keep the settings. See [Scene Viewer](scene-display-window-operations.md).

Click an image layer with `Ctrl` (`Cmd` on macOS) held, or with `Shift` held, to select several layers and change them together.

---

## 3D volume rendering

`Volume Rendering` offers these modes:

| Mode | What it shows |
|---|---|
| `Off` | No 3D volume rendering |
| `On` | Samples blended along each ray, weighted by opacity |
| `Max` | The brightest sample along each ray |
| `Min` | The dimmest sample along each ray |

`Gain` is shown in `On` mode only. It is exponential: the number shown is followed by the multiplier it produces, so 0 means x1.

`Resolution` sets how many samples are taken along each ray. Higher values look better and render more slowly. It is shown in every mode except `Off`.

Open the `Viewer` tab to change every image layer at once: `All image layers` holds `Volume Rendering`, `Blending` and `Opacity`. The `Settings` tab of a single layer changes that layer only. Volume rendering is visible only in a 3D panel.

---

## Troubleshooting

- **The image is black**: check that the layer and its channel are shown and that `Opacity` is not very low. Then click the channel to open its controls, and click `Auto` or `Reset` under `Intensity Adjustment`. Click `Auto` again for a stronger contrast stretch.
- **`Gain` is not shown**: it appears only when the mode is `On`.
- **Settings are gone after reopening the scene**: they were not saved. Press `Ctrl+S` (`Cmd+S` on macOS) in the viewer.

---

## Next

- [Scenes](scenes.md)
