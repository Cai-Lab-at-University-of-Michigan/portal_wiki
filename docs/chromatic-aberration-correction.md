---
tags:
   - imaging
   - chromatic-aberration
   - alignment
---

*Shift one channel of a tiled image against the others, using Virtual Stitching.*

Virtual Stitching can move one channel of each tile on its own, which shifts that channel against the others. The change is saved to the image, so it affects everyone who opens it, and only the image's owner, or a site administrator, can make it.

---

## Steps

1. Open Virtual Stitching with an image that holds several channels in one layer selected. See [Virtual Stitching](virtual-stitching.md). An image converted with `Split into separate layers per channel` has no `Move channels:` row, so this procedure does not apply.
2. Under `Tile Grid`, turn `Auto-select` off, then click `Select all`.
3. Under `Move channels:`, click `Deselect all`, then click the chip of the channel to correct. Leave the reference channel unselected.
4. Under `Move tile`, move the channel with the `X` and `Y` controls until its features line up with the reference channel in the viewer window. Positive X moves the channel right, and positive Y down.
5. Click `Confirm`.
6. Repeat for the next channel that needs a correction.

There are two `Deselect all` buttons. The one under `Tile Grid` clears the tile selection, and the one under `Move channels:` clears the channel selection.

How far a channel can move depends on the margin left when the image was converted. The panel grays out an axis that has no room.

---

## Troubleshooting

- **The correction disappeared**: `Auto-align`, `Refine`, `Reset` or `Restore` ran afterwards. Repeat the correction. `Discard` also reverts unconfirmed moves made in the current visit to the panel.
- **The move does not stay**: only the owner of the image, or a site administrator, can move tiles.
- **A channel chip has no color**: the chip still works. The color comes from the channel settings in the viewer.

---

## Next

- [Virtual Stitching](virtual-stitching.md)
