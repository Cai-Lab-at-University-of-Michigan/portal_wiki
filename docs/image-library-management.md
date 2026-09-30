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

Which entries you see depends on your role and on who owns the dataset. On a dataset that belongs to your group, a member sees only `View Details` and `Open Dataset`. A member cannot rename, share or delete it from `Library`. Ask a site administrator. See [Groups and Sharing](groups-and-sharing.md).

---

## Delete datasets

1. Open the row menu of the dataset and choose `Delete Dataset`.
2. Read the dialog. If the dataset is used in scenes, it lists them. The dataset's default scene is deleted with it. A scene you saved stays in `Scenes` without the dataset.
3. If layers were derived from the dataset, for example segmentations, tick the box that starts with `I understand`. Without the tick, the delete is refused with `Request failed (400)` and a message about child items.
4. Click `Delete`.

The deletion is permanent. For a file you converted, the original upload is not deleted and reappears in `Uploads`. A SISF folder you added with `Add to Library` has no separate original, so deleting the dataset deletes it. An image that has revisions cannot be deleted. The revisions are the rows with a `revision` badge. The delete is refused with `Request failed (409)`, so delete the revisions first.

To delete several datasets, click `Select` and tick the rows. The bar shows `N selected` and how many derived layers go with them. Click `Delete`, tick the box that starts with `I understand` if the dialog asks, and click `Delete` in the dialog. The `Shared with me` table does not offer `Select`.

---

## Troubleshooting

- **The image is black**: see [Basic Image Adjustments](basic-image-adjustments.md).

---

## Next

- [Scenes](scenes.md)
- [Groups and Sharing](groups-and-sharing.md)
