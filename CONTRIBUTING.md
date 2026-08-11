# Changing a dimension

The case is not a mesh you edit in CAD. It is drawn by a short script, so every dimension is a named number near the top of `src/enclosure.html`. Change the number, reload the page, download the part.

## How to do it

1. Open `src/enclosure.html` in a text editor.
2. Find the constants block after the `three-d-stage` setup. Everything is in millimetres, passed through `mm()`.
3. Edit a value.
4. Open the file in a browser. The model redraws with your change.
5. Pick the part you want and use the toolbar to download it as OBJ or GLB.

No build step, no toolchain, no npm. A browser and a text editor.

## The numbers worth knowing

| Constant | Means |
| --- | --- |
| `W`, `D` | Overall width and depth of the box |
| `R` | Outer corner radius |
| `T` | Wall thickness. `TR` is the thinner rear panel |
| `WALL_TOP` | Height of the shell wall, which sets the overall height with `SLOT` and `TOP_T` |
| `SLOT` | The floating gap between the wall top and the cover |
| `STANDOFF` | Height of the board above the base plate |
| `PX`, `PZ` | Corner post centres |
| `HX`, `HZ` | Board mounting hole centres, from the datasheet |
| `BZ` | How far the board sits forward of the box centre |
| `ports` | One row per rear connector: name, centre, width, height, top clearance |
| `SWX`, `LEDX` | Front window positions for the switches and LEDs |
| `CL` | Clearance added around every connector opening |

## If you are adapting this to a different board

Start with `ports`. Each entry is `[name, centre, width, height, top clearance]`, with the centre measured from the middle of the box, positive to the right seen from the rear. Then set `HX` and `HZ` to your board's mounting holes, and `PCB_W` and `PCB_D` to its outline. Most of the rest follows.

## Keeping the drawings honest

`docs/drawings.html` repeats the same constants at the top of its own script. If you change the model, change them there too, or the drawings will quietly disagree with the parts. The exploded image in the build sheet is a render — regenerate it from the model if the geometry moves.

## Pull requests

Say what you printed and what fitted. A photo of the failure is worth more than a description of it.
