---
tags:
   - scenes
   - viewer
---

*This tutorial explains what a scene is and how to manage scenes.*

---

## What a scene is

A dataset in `Library` is the image data. A scene is a saved view of one or more
datasets: which layers are loaded, how they are positioned, and how they are
displayed. Opening a dataset opens it in a scene, and annotation happens in a
scene, because a segmentation layer is a layer within it.

---

## Managing scenes

Open `Scenes` in the sidebar. Each scene's `Actions` menu offers:

- `Open Scene` opens it in the viewer.
- `Edit Scene` changes the title and description.
- `Duplicate Scene` copies it, including its layers and settings.
- `Move Scene To Folder` files it under a folder.
- `Share Scene` creates a link. See below.
- `Download Scene` saves the scene state as a `.json` file. This is the view
  description, not the image data.
- `Delete Scene` removes the scene. The datasets it referred to are not deleted.

Folders are created and renamed on the same page, and hold scenes only.

---

## Sharing a scene

`Share Scene` creates a link, which you can also reach from the `Share` icon in
the viewer.

The recipient needs a portal account. Opening the link signs them in and adds the
scene to their own `Scenes` list as a copy. Changes they make there do not reach
your scene, and changes you make afterwards do not reach theirs.

The link carries the scene as it was when the link was created. Save the scene
first with `Ctrl+S` (Windows/Linux) or `Cmd+S` (macOS) in the viewer.

---

### Troubleshooting

- **A shared link shows an older view**: the link holds a snapshot. Save the
  scene, then create a new link.
- **A scene opens empty**: its dataset may have been deleted from `Library`.
