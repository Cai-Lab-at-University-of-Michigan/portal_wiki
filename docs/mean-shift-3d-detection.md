---
tags:
   - annotation
   - mean-shift
   - spot-detection
   - algorithm
---

*This tutorial guides the process for using the 3D Mean Shift algorithm to detect fluorescent spots in microscopy images.*

---

## Overview

**3D Mean Shift** is an unsupervised spot detection algorithm for fluorescent microscopy. It automatically identifies bright spots (e.g., synapses, puncta) without requiring manual seed placement. Detected points are saved as an annotation layer and can be downloaded as CSV.

---

## Getting Started

1. Open an image scene and select an **image layer** in the right sidebar
2. Open the **Interactive Annotation** panel
3. Click **Lock View** to define the detection region
4. Select the **Algorithm** tool, then choose **3D Mean Shift**

The parameter panel and a **Run** button will appear.

> Lock a tight region for faster computation. Detection runs on the locked bounding box only.

---

## Configure Parameters

Adjust parameters before running. Hover over a parameter name for its description.

### Key Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| **Intensity Threshold** | 65 | Minimum raw voxel intensity to consider |
| **BG Sub Threshold** | 5.0 | Minimum background-subtracted intensity |
| **Bandwidth** | 4.0 | Spatial radius for the Mean Shift kernel — larger values merge nearby peaks |
| **Merge Distance** | 7.0 | Peaks closer than this distance are merged into one |
| **SNR Threshold** | 3.0 | Minimum local signal-to-noise ratio for post-filtering (0 = disable) |

### Fine-Tuning Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| **Min Component Size** | 3 | Minimum connected component size for seed generation |
| **Anisotropy Z** | 1.0 | Z-axis voxel size ratio (increase if Z resolution is lower than XY) |
| **Boundary Margin** | 2 | Voxels near volume edges use stricter SNR filtering |
| **Adaptive BW** | Off | Scale bandwidth per-seed based on local SNR |

---

## Run Detection

1. Configure parameters as needed
2. Click **Run 3D Mean Shift**
3. Wait for the algorithm to complete — detected points are displayed as annotations in the viewer
4. A result badge shows the number of detections (e.g., "Detected 42 points")

> Detection can be run multiple times with different parameters. Each run replaces the previous result.

---

## Download Results

After detection, click the **CSV** button to download all detected point coordinates as a CSV file.

---

## Region Selection

By default, the algorithm operates on the locked viewport region. To specify a custom bounding box:

1. Switch from **View** to **Manual** in the region selector
2. Enter X, Y, Z start and end coordinates manually

---

## Tuning Guide

**Detecting too many false positives?**

- Increase **Intensity Threshold** to ignore dim voxels
- Increase **SNR Threshold** to require stronger signal
- Increase **BG Sub Threshold** to filter out background fluctuations

**Missing real spots?**

- Lower **Intensity Threshold** and **BG Sub Threshold**
- Lower **SNR Threshold** (or set to 0 to disable filtering)
- Decrease **Bandwidth** if nearby spots are being merged

**Too many detections in the same spot?**

- Increase **Merge Distance** to consolidate nearby peaks

**Z-axis detections seem off?**

- Adjust **Anisotropy Z** to match your data's voxel size ratio (e.g., if Z step is 3x the XY pixel size, set to 3.0)

---

## Troubleshooting

- **No points detected**
    - Lower **Intensity Threshold** — your data may have different intensity range
    - Check that the locked region contains visible spots

- **Detection runs slowly**
    - Lock a smaller region of interest
    - Increase **Intensity Threshold** to reduce the number of candidate voxels

- **Points appear at wrong Z positions**
    - Adjust **Anisotropy Z** to match your imaging setup

- **Other issues**
    - Contact the site administrator

---
