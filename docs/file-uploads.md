---
tags: 
   - upload
   - globus
---

*Transfer files to the portal with Globus and find them under `Uploads`.*

---

## Set up Globus

To send files from your own computer, install Globus Connect Personal and choose the folders you want to make available for transfer. See the [Globus installation and configuration guide](https://docs.globus.org/globus-connect-personal). You also need a Globus login and an upload collection that the site administrator assigns to your account. Until one is assigned, `Upload Files via Globus` shows `No endpoint assigned. Please contact administrator.`

---

## Steps

1. Open `Uploads`.
2. If your account belongs to a group, the top of the page shows `My Files` and a button named after the group. Choose the group button to upload to the group's shared folder.
3. Click `Upload Files via Globus`. For an account that has only a group collection, the button reads `Upload via <group> Globus`. Globus opens in a new tab with the portal's collection preselected as the destination.
4. In the other panel, choose your own computer's collection, select the files or folders, and start the transfer.
5. Wait until Globus reports that the transfer has completed.
6. Return to the portal and click `Scan & Refresh`. The new files appear in the list.

New files appear only after `Scan & Refresh`. The status of a running conversion refreshes by itself.

---

## The Uploads list

| Column | Shows |
|---|---|
| `Name` | The file or folder. A folder expands in place to show its contents. An acquisition folder (for example Squid) or a TIFF series is one row. |
| `Type` | The format, for example `TIFF` or `NIFTI`. Only rows of a format the portal can convert offer `Convert to SISF`. |
| `Size` | The size of the file or folder. |
| `Status` | A dash until conversion. `Processing...` with a percentage while a conversion runs. Then `Added` (the dataset is in `Library`) or `Converted` (converted but not in `Library`, see [Convert to SISF](file-conversion.md)). |
| `Modified` | When the file last changed. |
| `Actions` | The row menu. |

Only formats the portal can use are listed. A file in another format does not appear after a scan. See Supported sources in [Convert to SISF](file-conversion.md) for the formats.

---

## Delete uploads

1. Open the row menu and choose `Delete File` or `Delete Folder`.
2. Confirm with `Remove`.

To delete several items, click `Select`, tick the rows, and click `Delete`, then click `Delete` in the dialog. A ticked folder takes everything inside it.

Deleting an upload removes only the raw file. A dataset already in `Library` keeps its converted copy.

The row menu depends on the row. It offers `Convert to SISF`, `Already Converted (Redo?)` after a conversion, or `Conversion Ongoing...` while one runs, plus `Rename File` and the delete entry. `Re-detect & Refresh` reads a folder again, for example one that was still uploading when it was scanned.

---

## Troubleshooting

- **`You don't have any files yet` after a transfer**: click `Scan & Refresh`. Also check that Globus reports the transfer as complete, and that you are looking at `My Files` or the group you uploaded to.
- **`No endpoint assigned. Please contact administrator.`**: your account has no upload collection yet. Ask the site administrator to assign one.
- **Your computer's collection does not appear in Globus**: make sure Globus Connect Personal is running and that the folder is shared in its settings.
- **The portal's collection is not the destination**: close the Globus tab and click `Upload Files via Globus` again. If it still fails, ask the site administrator.
- **A colleague cannot see the upload**: files in `My Files` are private to your account. See [Groups and Sharing](groups-and-sharing.md).

---

## Next

- [Convert to SISF](file-conversion.md)
