---
tags:
   - groups
   - sharing
---

*Share data with colleagues through a group space, dataset sharing and scene links.*

---

## Group space

A group space is a shared upload area with shared datasets. A site administrator creates it (`Admin`, `Group Workspaces`, `Add Workspace`) and adds its members under `Sharing Groups`, in the group that has the same name. You cannot join one yourself, and the `Organization/Group` text in `Settings` is only a label. Group spaces exist only on sites where a site administrator has set one up.

- In `Uploads`, a member sees two buttons at the top: `My Files` and a button named after the group. Files in `My Files` are private to you. Choose the group button before you click `Upload Files via Globus` to upload to the group's shared folder. Every member can scan and convert files in that folder. A file converted there belongs to the group.
- In `Library`, datasets that belong to the group appear with your own, marked with a `Group` badge. A member can open a group dataset and make a segmentation on it. That segmentation belongs to the member alone.
- For a member, the row menu of a group dataset offers `View Details` and `Open Dataset`. A member cannot rename, share or delete a group dataset, make it public, or use `Edit Metadata` or `Link as Segmentation` on it. If a member ticks a group dataset under `Select` and confirms `Delete`, the toast `1 of 1 could not be deleted` shows `Not enough permissions`, and the dataset stays. Ask a site administrator.
- People who are not members of the group see no group button in `Uploads` and no group datasets in `Library`.
- If you see only the heading `My Files`, your account is not a member of a group space.

---

## Share a dataset

1. In `Library`, open the row menu of the dataset and choose `Share Dataset`. Only the owner and people with the `Admin` role see it.
2. Under `Add people or groups`, type the first letters of a person's name or organization, or a full email address, and pick the person from the list. To share with a group, choose it under `Or add a group…`.
3. Choose a role, then click `Add`.

Changes apply at once, and there is no Save button. Change a role in the role picker of a row, and remove access with the X on that row. The people you add need an activated account on this site. A new account cannot be found until a site administrator activates it. The dataset appears in their `Library`, in the `Shared with me` table.

| Role | Can |
|---|---|
| `Viewer` | Open and read the dataset. |
| `Editor` | Also change the title and description, and change the dataset's content, for example edit a segmentation someone shared with you. |
| `Admin` | Also manage who has access, by giving `Viewer` and `Editor`. |

A `Viewer` can still make their own segmentation on the image. The owner can do everything, including delete the dataset and give `Admin`. The `Admin` role is an access level for one dataset. It is not a site administrator.

Only the owner, or a site administrator, sees `Make public (anyone signed in can view)`. It gives every signed-in user read-only access, but the dataset is not listed for them, so send them a scene link. There is no link for people without an account.

A segmentation you create on a shared or group image belongs to you alone. Share it from `Library` if others should see it.

---

## Share a scene

1. Open the row menu of the scene in `Scenes` and choose `Share Scene`, or click the share icon in the top bar of the viewer.
2. Click `Create link`, then `Copy`, and send the link.

The recipient must be signed in, even though the dialog text suggests otherwise. If they are not, the link takes them to the login page, and they open the link again after signing in. The scene is added to their `Scenes` list as a copy. The link shares the view, not the data: the recipient sees only the layers of datasets that are shared with them. Share the datasets as well with `Share Dataset`.

See [Scenes](scenes.md).

---

## Troubleshooting

- **A colleague cannot see my upload**: files in `My Files` are private. Convert the file, then share the dataset, or upload to the group space.
- **The group button is missing**: your account is not a member of a group space. Ask the site administrator.
- **A shared dataset is not in `Library`**: look in the `Shared with me` table below the main list.
- **A shared scene opens with fewer layers**: the datasets in it are not shared with the recipient.
- **A message says you have viewer access and the action needs editor access**: ask the owner for the `Editor` role.

---

## Next

- [Library](image-library-management.md)
- [Scenes](scenes.md)
