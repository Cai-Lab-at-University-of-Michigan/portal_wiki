---
tags:
   - scenes
   - viewer
---

*This tutorial explains what a scene is and how to manage scenes.*

---

## What a scene is

A dataset in `Library` is the image data. A **scene** is a saved view of one or
more datasets: which layers are loaded, how they are positioned, and how they are
displayed. Opening a dataset opens it in a scene, and annotation always happens
in a scene, because a segmentation layer is a layer within it.

Two people can hold different scenes over the same dataset without affecting each
other.

---

## Managing scenes

Open `Scenes` in the sidebar. Each scene's `Actions` menu offers:

- `Open Scene` opens it in the viewer.
- `Edit Scene` changes the title and description.
- `Duplicate Scene` copies it, including its layers and settings. Use this before
  trying a different arrangement.
- `Move Scene To Folder` files it under a folder.
- `Share Scene` creates a link.
- `Download Scene` saves the scene state as a `.json` file. This is the view
  description, not the image data.
- `Delete Scene` removes the scene. The datasets it referred to are not deleted.

Folders are created and renamed on the same page. They organise scenes only.

---

## Sharing a scene

`Share Scene` produces a link that opens the scene read-only. Anyone with the
link can open it without an account, so treat it as public.

To save the current state before sharing, press `Ctrl+S` / `Cmd+S` in the viewer.

---

### Troubleshooting

- **A shared link shows an older view**: the scene was not saved after the change.
  Reopen it, press `Ctrl+S` / `Cmd+S`, and share again.
- **A scene opens empty**: its dataset may have been deleted from `Library`.
