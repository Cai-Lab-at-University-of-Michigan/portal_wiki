---
tags: 
   - nninteractive
   - annotation
---

*This tutorial guides the process for using nnInteractive for AI-assisted image annotation.*

---

## First-time Usage

**nnInteractive** runs in a separate environment.  
Please contact the site administrator to set up your account before first use.

Ignore the "Authenticate" window and close it.

---

## Prepare ROI Image Data

1. Open an image dataset and select an ROI  
   (refer to the [Basic Operations Guide](scene-display-window-operations.md)).
2. In the ROI Selection dialog, click `Annotate`.  
   This will download the ROI image data to your nnInteractive workspace.

---

## Annotate

1. Click `nnInteractive` in **Quick Access** and log in with your credentials.
2. Your ROI data will appear in the `data` folder on your desktop.  
   This folder is **protected**, meaning you **cannot modify or delete files** directly inside it.
3. To work on a file:
   - Create a new folder on your desktop
   - Drag the desired ROI file from the `data` folder into your new folder
   - Perform annotation on the copied file

This process ensures the original ROI dataset remains intact.

For instructions on how to use nnInteractive tools, see the
[nnInteractive documentation](./tutorials/nninteractive-access-and-usage-guide.pdf).

---

## Continue Previous Work

It is definetly frustrated if the noVNC disconnects or napari just crashs. But we can continue previous work, with some loss :( though. First, the segmentation is saved automatically every **15 minutes**.

To load previous progress:

1. Open the image and initialize it
2. Open the autosaved segmentation, select it, and click **Load Previous Instances** on the right
3. Continue your work

If you have an unfinished object (e.g., due to a crash):

1. Change the class ID to that object's ID
2. Click **Load Single Object** on the right
3. Continue working on that object as you usually do

---

## Troubleshooting

- **I do not see the `nnInteractive` option in Quick Access**
  - Your account may not be activated yet  
  - Contact the site administrator

- **I cannot log in**
  - Ensure your nnInteractive account has been created  
  - Try resetting your credentials if applicable

- **My ROI file is not appearing in the `data` folder**
  - Confirm the ROI selection was downloaded (click `Annotate` again)
  - Check that the upload/conversion job has completed in the portal
  - Restart nnInteractive and refresh the folder view

- **I cannot delete or move files inside `data`**
  - This is expected — the folder is protected  
  - Copy files to a new workspace folder instead

- **Annotation changes are not saved**
  - Ensure you are editing files in your own folder, not `data`
  - Confirm local disk permissions are not restricted

- **Viewer loads but image is blank**
  - Try re-opening the file  
  - If the problem persists, the ROI conversion may have failed — contact the administrator

---
