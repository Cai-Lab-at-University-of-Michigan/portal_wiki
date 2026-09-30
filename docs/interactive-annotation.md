---
tags:
   - annotation
   - segmentation
---

*Segment structures in a scene with the Interactive Annotation panel, commit the result, and export it.*

---

## Steps

1. Open a dataset from `Library` (`Open Dataset`) or a scene from `Scenes` (`Open Scene`). The viewer opens in the viewer window. Keep it open: the panel works on the scene in that window.
2. In the main window, click `Interactive Annotation` in the sidebar, under `Plugins`.
3. Choose a segmentation layer. In the viewer window, open the `Layers` tab, click the image layer, and open its `Info` tab. Under `Segmentation Layer`, click `New`, choose a resolution in `New Segmentation Layer`, and click `Create`. To use an existing layer, click `Load` instead.
    - The dialog marks the full-resolution option `RECOMMENDED` (also shown as `(full resolution)`). A coarser layer is smaller, but the detail it drops cannot be recovered, and some tools need full resolution.
    - Creation runs as a job. The viewer may switch to a copy of the scene. If the new layer is not in the layer list, open the scene again from `Scenes`.
    - A segmentation layer you create belongs to you alone. Share it from `Library` if others should see it.
4. Click the segmentation layer in the layer list to select it.
5. In the panel, choose a tool: `Brush`, `Eraser`, `Merge`, `Split`, `Algorithms` or `AI Model`. Hover over a grayed tool to read the reason. On an image layer only `Algorithms` can be used.
6. Zoom and pan the viewer to the region you want, then click `Lock View`. The button stays grayed out until a tool is chosen, because the tool decides how large a region can be locked. The line under the button shows the size of the region against the limit for the tool. `Reset View` returns the viewer to the locked region, and `Unlock` releases it.
7. Annotate with the tool, as described below.
8. Click `Commit` to write the result into the segmentation layer. `Merge` and `Split` write at once and need no `Commit`.
9. To export the layer, select the segmentation layer, choose `Algorithms` and click `Export TIFF`.

For most tools the lock covers the region shown in the viewer, with Z centered on the current slice. With `AI Model` the lock can take the full depth and be read at a coarser resolution. The line under the button shows what will be locked.

`Hand`, the first icon in `Tools`, lets you drag to pan. Choosing another tool turns it off.

---

## Brush and eraser

Choose `Brush` (`D`) and paint in the viewer. `Eraser` (`E`) removes voxels. Both need the lock. `Brush Settings` holds the brush size and color. Painting with segment 0 selected also erases. Erasing voxels that are already committed takes effect when you `Commit`.

---

## Segments

The `Segmentation` section lists the segments as numbered chips.

- `+ New` starts the next segment. `Next` moves to the following segment, and from the last one it starts a new segment. `Prev` stops at segment 1.
- Click a chip to select that segment. The viewer jumps to it only if the segment already has content. The multi-select button next to `Clear` changes chip clicks into choosing segments for `Clear` or `Delete`. Switch it off to select normally.
- `Clear` empties the selected segment inside the locked region and keeps its number. `Delete` also retires the number. Both ask for confirmation and cannot be undone.

---

## Merge and Split

`Merge` combines segments, and `Split` separates a segment into its connected pieces and removes pieces that are too small to keep. Both act on committed voxels only, so `Commit` first if you just painted the segments.

Both work inside a region that you draw in the viewer window with `B`, not inside the locked region. Only voxels inside that box change, including its depth.

1. Choose `Merge` or `Split`. For `Split`, the `Split Segment` button stays grayed out until you click `Lock View`.
2. Draw the region. In the viewer window, press `B` at one corner on one slice, scroll to another slice, wait a moment, and press `B` at the opposite corner. See [Scene Viewer](scene-display-window-operations.md#select-and-download-a-region).
3. Hover over a segment on a slice that shows it. The panel shows `Hovered:`, the segment number and its buttons, only while the pointer is over the segment.
4. For `Merge`, click `Add as Source` for each segment to fold in, then hover over the segment to keep and click `Set as Target`. The sources are listed under `Source Segments (will be replaced):` and the target under `Target Segment (merge into):`. For `Split`, click `Set as Split Target`. To set the target, or the segment to split, by number instead of hovering, type it in the `Enter ID` box and press `Enter`. Sources can only be added with `Add as Source`.
5. Click `Merge N → <target>` (`N` is the number of sources) or `Split Segment <number>`.

`Merge` and `Split` change the layer at once, without `Commit`. `Undo` and `Redo` do not reverse them. Only the most recent merge and the most recent split can be reverted, with `Undo Last Merge` or `Undo Last Split`. After a split, `Last Split Result:` lists the new segments.

---

## Algorithms

- `Flood Fill` grows a region from seed points. See [Flood Filling](flood-filling-annotation.md).
- `3D Mean Shift` detects spots and writes points. See [3D Mean Shift](mean-shift-3d-detection.md).

---

## Model runs

The `AI Model` tool runs segmentation models on a GPU worker. It is available only on sites configured for it, and it needs a segmentation layer to be selected.

1. Choose a model in the model list at the top right of the `AI Model` panel. The list shows the models that apply to the current image and site.
2. Choose a prompt type, then click in the viewer. The panel shows the prompt types the chosen model supports. Use `Pos` for a prompt on the object and `Neg` for a prompt on the background.
3. Click `Run AI Segmentation`, or switch on `AutoRun` to run after every prompt.

Each prompt refines the mask, so start with one and add prompts where the result is wrong. `Clear Prompts` removes the prompts and keeps the mask. `Undo Prompt` removes the last prompt. `Next Object` keeps the mask and starts a new segment. On a multi-channel image, the channel list selects the channel the model reads.

While a run is in progress, `Running AI segmentation` shows where it is. If many runs are waiting, the notification `Queue is busy` appears. Nothing is written, and the prompts are kept, so wait a moment and run again.

For whole-volume microCT segmentation without prompts, see [MicroCT Segmentation](microct-segmentation.md).

---

## Commit

`Commit` writes the uncommitted work into the selected segmentation layer. Until then the work is a temporary mask and is not part of the layer.

- A commit cannot be undone, and it clears the prompts.
- `Don't overwrite existing segments` keeps voxels that already belong to another segment when you commit. The eraser always erases.
- `Undo` and `Redo` apply to uncommitted work.
- The key `W` asks for confirmation first. `Unlock` asks before it discards uncommitted work.

---

## Export

Select the segmentation layer, choose `Algorithms`, and click `Export TIFF`. The committed layer downloads as a TIFF named after the segmentation's title in `Library`, for example `<dataset title> - Segmentation #1.tif`. It exports the whole layer at the resolution you chose when you created it, not only the locked region, so use it on layers small enough for a single download.

---

## Keyboard shortcuts

Shortcuts act on the window that has the focus. In the main window they work only while a single-channel segmentation layer you can edit is selected, and not while you type in a field. `[`, `]` and `Esc` work in the viewer window only.

| Key | Action |
|---|---|
| `D` | Brush |
| `E` | Eraser |
| `[` `]` | Brush size |
| `1` to `4` | Prompt types, in the order the panel shows them |
| `P` | Switch prompts between `Pos` and `Neg` |
| `T` | Toggle `AutoRun` |
| `S` | Run the model (needs a prompt type and one prompt) |
| `C` | `Clear Prompts` (in Flood Fill, `Clear` removes the seeds) |
| `U` | `Undo Prompt` |
| `Ctrl+Z` (`Cmd+Z` on macOS) | Undo |
| `Ctrl+Shift+Z` (`Cmd+Shift+Z` on macOS) | Redo |
| `W` | Commit, after a confirmation |
| `X` | Clear the selected segment, after a confirmation |
| `N` / `M` | Next / previous segment |
| `G` | Select the segment under the pointer. Over empty space it selects segment 0, which erases. |
| `L` | Lock or unlock the view (choose a tool first) |
| `R` | `Reset View` |
| `Esc` | Clear prompts and uncommitted strokes, and deselect the tool, without asking |
| `Space` | Hold to pan |

Arrow keys are ignored while the view is locked, unless the `Hand` tool is on.

---

## Troubleshooting

- **A tool is grayed out**: hover over it for the reason. Choose a single-channel segmentation layer. Only `Algorithms` also opens on an image layer.
- **`Lock View` is grayed out**: choose a layer and a tool first. If both are set, the region is too large for the tool: zoom in, or lower the Z value next to the size line. A notice under the button says when zooming is the only fix. For `AI Model`, wait for the model list to load.
- **The panel says `Lock the view first to enable tools`**: choose a tool first, then lock. The notice is out of date.
- **A stroke does nothing**: lock the view first.
- **`Something went wrong!` with `No bounding box provided and no ROI set`** on `Merge` or `Split`: draw a region with `B` first.
- **`Something went wrong!` with `Internal Server Error`** on `Merge` or `Split`: the region is incomplete, has no depth, or is too large. Clear it with a right-click in the viewer window and draw a smaller one on two different slices, with a pause between the two presses of `B`.
- **The panel shows a notice that begins `Please select a layer to begin`**: click a layer in the viewer window's `Layers` tab. After you open a different scene, pick the layer again.
- **The new segmentation layer is not in the layer list**: open the scene again from `Scenes`.
- **The result disappeared after unlocking**: it was never committed. Click `Commit` before `Unlock`.
- **The tools are grayed and mention view-only access**: the layer is shared with you as `Viewer`. Create your own segmentation on the image and annotate there.
- **`A commit is in progress for this scene`**: wait for the commit to finish, then repeat the step. Nothing is lost.
- **`Please open a scene to use Interactive Annotation`**: the viewer window is closed. Open the dataset or scene again.

---

## Next

- [Flood Filling](flood-filling-annotation.md)
- [3D Mean Shift](mean-shift-3d-detection.md)
- [MicroCT Segmentation](microct-segmentation.md)
