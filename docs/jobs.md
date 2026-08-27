---
tags:
   - jobs
---

*This tutorial covers the Jobs page, where background work is tracked.*

---

## Overview

Work that takes longer than a request runs as a background job: SISF conversion,
flatfield fitting, tile stitching, spot detection, and microCT segmentation. Open
`Jobs` in the sidebar to see them.

Each row shows the job type, its status, and progress. You can leave the page or
close the browser while a job runs.

---

## Actions

The `Actions` menu shows what the job's current status allows:

- `View Details` shows the parameters the job was submitted with, and the error
  message if it failed.
- `Start Job` submits a job that was created but never sent to a worker.
- `Cancel Job` stops a job that is pending, running, or paused.
- `Restart Job` submits it again. It appears once the job has stopped, whether it
  was paused, canceled, or failed.
- `Delete Job` removes the row.

---

### Troubleshooting

- **A job stays at 0%**: it is queued and waiting for a free worker.
- **A job failed**: open `View Details` and read the error. For conversion, the
  usual causes are an image size or channel count that does not match the file.
