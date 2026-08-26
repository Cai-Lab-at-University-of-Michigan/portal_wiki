---
tags:
   - jobs
---

*This tutorial covers the Jobs page, where background work is tracked.*

---

## Overview

Work that takes longer than a request runs as a background job. This includes
SISF conversion, flatfield fitting, tile stitching, registration, spot detection,
and microCT segmentation. Open `Jobs` in the sidebar to see them.

Each row shows the job type, its status, and progress. You can leave the page or
close the browser while a job runs.

---

## Actions

- `View Details` shows the parameters the job was submitted with, and the error
  message if it failed.
- `Cancel` stops a running or pending job.
- `Restart` submits the same job again, which is useful after fixing the cause of
  a failure.

---

### Troubleshooting

- **A job stays at 0%**: it is queued and waiting for a free worker. If it does
  not start at all, contact the site administrator.
- **A job failed**: open `View Details` and read the error. For conversion, the
  usual causes are an image size or channel count that does not match the file.
