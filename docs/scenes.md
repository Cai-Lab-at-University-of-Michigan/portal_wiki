---
tags:
   - scenes
   - viewer
---

*Keep, organize and share saved views of your datasets.*

---

## What a scene is

A dataset in `Library` is the image data. A scene is a saved view of one or more datasets: which layers are loaded, how they are positioned, and how they are displayed. Annotation happens in a scene, because a segmentation layer is a layer within it.

A dataset opened from `Library` uses a default scene, marked with a Default Scene badge in the viewer. Default scenes are not listed under `Scenes`. Any other scene carries a Composed Scene badge: a scene you saved, duplicated, added or composed, and the scene the viewer creates when you add a layer or a segmentation to a default scene.

---

## Steps

1. Open a dataset from `Library`. See [Library](image-library-management.md).
2. In the viewer window, press `Ctrl+S` (`Cmd+S` on macOS). Enter a `Scene Name` and click `Save`.
3. Open `Scenes` in the sidebar. The scene is listed there. Double-click it to open it again.

---

## Other ways to create a scene

- Click `Compose Scene` on the `Scenes` page to build a new scene from several datasets, or from the datasets of existing scenes. Display settings are not copied, so set them again in the new scene.
- Choose `Duplicate Scene` on an existing scene.
- Click `Add Scene`, enter a `Title`, choose a scene `.json` file, such as one saved with `Download Scene`, and click `Save`.

---

## Manage scenes

Open `Scenes` in the sidebar. Double-click a scene to open it, or open its row menu in the `Actions` column:

- `Open Scene` opens it in the viewer, after you click `Continue`, and replaces the scene you already have open.
- `Download Scene` saves the scene state as a `.json` file. It describes the view, not the image data.
- `Duplicate Scene` copies the scene as `<title> (Copy)`, with its layers and settings.
- `Edit Scene` changes the title and description. It can also replace the view from a `.json` file.
- `Move Scene` opens `Move Scene to Folder`. Choose a folder and click `Move`.
- `Share Scene` creates a link. See [Groups and Sharing](groups-and-sharing.md).
- `Delete Scene` removes the scene. The datasets it used are not deleted.

`Create Folder` adds a folder. `Delete Folder` keeps the scenes in it and moves them to the top level.

To act on several scenes, click `Select`, tick the rows, and choose `Move Selected`, `Duplicate (N)` or `Delete`.

---

## Troubleshooting

- **`Scenes` is empty after you opened a dataset**: default scenes are not listed. Press `Ctrl+S` (`Cmd+S` on macOS) in the viewer to keep one.
- **A shared link shows an older view**: the link holds the scene as it was when the link was created. Save the scene, then create a new link.
- **A scene opens without some layers**: a dataset in it may have been deleted from `Library`, or it is not shared with you.
- **A new segmentation layer is not in the layer list**: open the scene again from `Scenes`.

---

## Next

- [Scene Viewer](scene-display-window-operations.md)
- [Interactive Annotation](interactive-annotation.md)
