---
tags:
   - jobs
---

*Follow background work and find out why a job failed.*

---

## Overview

Conversions and other long operations run as background jobs. Which operations exist depends on the site. Open `Jobs` in the sidebar to see them. You can leave the page or close the browser while a job runs.

Each row shows:

| Column | Shows |
|---|---|
| `Title` | What the job does and for which dataset. |
| `Type` | The kind of job, for example a conversion. |
| `Status` | One of the values below. |
| `Progress` | A bar with a percentage. |
| `Updated` | When the job last changed. |
| `Actions` | The row menu. |

The list refreshes by itself while a job is `PENDING` or `STARTED`. Some statuses are rare: no button pauses a job, so you will seldom see `PAUSED`.

| Status | Meaning |
|---|---|
| `DRAFTING` | Created but not yet sent to a worker. |
| `PENDING` | Queued, waiting for a free worker. |
| `STARTED` | Picked up by a worker. It may still be at 0% if the worker is busy. |
| `PAUSED` | Stopped, and can be restarted. |
| `SUCCESS` | Finished. |
| `FAILURE` | Ended with an error. |
| `CANCELED` | Canceled, by you or because a job it depended on was canceled. |

---

## Actions

Click a row to open `Job Details`, or open its row menu in the `Actions` column. The menu offers what the job's status allows:

- `View Details` opens `Job Details`: the parameters the job was submitted with and, when there is one, `Result`. An error message appears in red under `Result`.
- `Start Job` sends a job that was created but never submitted.
- `Restart Job` submits a stopped job again. It is offered for `PAUSED`, `CANCELED` and `FAILURE`.
- `Cancel Job` stops a job that is `PENDING`, `STARTED` or `PAUSED`. A canceled job cannot be resumed, only restarted.
- `Delete Job` removes the row. It is grayed out while a job is `PENDING` or `STARTED`, so cancel it first.

---

## Troubleshooting

- **A job stays at 0%**: it is queued or waiting for a busy worker. Leave it. If it never starts, contact the site administrator.
- **A job shows `FAILURE`**: open `View Details` and read `Result`.
- **A conversion shows `SUCCESS`, but the dataset is not in `Library`**: `Result` ends with `auto-register skipped` and the reason, for example that a segmentation does not match its parent image. See [Convert to SISF](file-conversion.md).

---

## Next

- [Convert to SISF](file-conversion.md)
- [Library](image-library-management.md)
