---
tags: 
   - image
---

*Open, edit, share and delete the datasets you have converted.*

---

## The Library list

`Library` (the page is titled `Library Management`) lists the datasets in your account and in your group's space, most recently updated first. The columns are `Title`, `Description`, `Type`, `Dimensions`, `Size`, `Updated` and `Actions`. Click a row to see the dataset's details. Click `Type` to filter by `Image`, `Segmentation`, `Pointcloud` or `Mesh`.

A dataset owned by your group carries a `Group` badge. Segmentations and channels made from a dataset are listed under it: click the arrow at the start of the row to expand. Datasets that others shared with you are in the second table, `Shared with me`, with a `Your access` column.

A dataset appears here when a conversion finishes. See [Convert to SISF](file-conversion.md).

---

## Open a dataset

1. Open the row menu in the `Actions` column of the dataset's row.
2. Choose `Open Dataset`.
3. The dialog explains that a default scene is created for the dataset and that any scene you have open is replaced. Click `Continue`.

The viewer opens in a new window, the viewer window. See [Scene Viewer](scene-display-window-operations.md).

---

## Row menu

| Entry | Use it to |
|---|---|
| `View Details` | See the type, data type, dimensions, sizes and the scenes that contain the dataset. |
| `Open Dataset` | Open the dataset in the viewer. |
| `Edit Dataset` | Change the title and description. |
| `Edit Metadata` | Correct the voxel size or tile overlap (saved as a new revision) or the channel details, without converting again. See [Edit Metadata](edit-metadata.md). |
| `Set as current revision` | On a revision, mark it as the current version. For the owner or a site administrator. |
| `Link as Segmentation` | Turn this dataset into a segmentation of another image. Pick the parent image and click `Link`. The dimensions must match exactly, and the dataset must have one channel. |
| `Share Dataset` | Give people access. See [Groups and Sharing](groups-and-sharing.md). |
| `Delete Dataset` | Remove the dataset. |

You see only the entries your access allows. Members of a group can open the group's datasets. Changing, sharing or deleting them is for a site administrator.

---

## Delete datasets

1. Open the row menu of the dataset and choose `Delete Dataset`.
2. Read the dialog. It lists the scenes that use the dataset.
3. If layers were derived from the dataset, for example segmentations, tick the box that confirms they are deleted too.
4. Click `Delete`.

The deletion is permanent. For a file you converted, the original upload is not deleted and reappears in `Uploads`. A SISF folder you added with `Add to Library` has no separate original, so deleting the dataset deletes it. An image with revisions, the rows with a `revision` badge, cannot be deleted until its revisions are deleted.

To delete several datasets, click `Select`, tick the rows, and click `Delete`. The `Shared with me` table does not offer `Select`.

---

## Troubleshooting

- **The image is black**: see [Basic Image Adjustments](basic-image-adjustments.md).
- **`Open Dataset` opens no window**: check that your browser is not blocking pop-ups for this site. The confirmation message appears even when the browser blocks the window.

---

## Next

- [Scenes](scenes.md)
- [Groups and Sharing](groups-and-sharing.md)
