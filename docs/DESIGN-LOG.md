# How this design got here

Four printed revisions. Each one failed in a way that changed the next. This is the record, mostly so nobody repeats the mistakes.

## The brief

A finished-looking box for a Toradex Mallow carrier board with a Verdin SoM and a passive heatsink. It had to hold the board, expose the five rear connectors, allow access to the bottom-side connectors, and look like a product rather than a lab fixture. The starting point was a skeleton frame used on the bench.

## Rev A — corner pillars

116 × 88 × 43 mm, 10 mm corner radius. Four Ø9 pillars at the corners, inset from the walls, each carrying an M3 from the base plate and a 5 × 2 magnet in its head for the floating lid. Board mounted on standoffs in the base plate.

**Printed. Three failures.**

1. The base plate's standoffs (Ø8 at 47/33, on the board's own mounting holes) and the shell's pillars (Ø9 at 51.5/37.5) overlapped by about 2 mm. The two parts physically would not go together.
2. The pillars sat inside the board footprint, so the board could not travel far enough back to reach the rear panel.
3. At 116 × 88 the shell was 16 mm larger than the 100 × 72 board in both directions. Nothing lined up because nothing was located.

## Rev B — standoffs moved into the shell

107 × 79 mm, cavity sized to the board plus 1 mm per side. Corner pillars deleted. The four standoffs became part of the shell, standing on the board's own Ø3.2 holes and webbed into the side walls. Lid magnets moved to four bosses in the cavity corners, 16 mm above the PCB so they cleared the connectors and the heatsink.

This solved the collision, but introduced a worse problem.

**Printed. Three failures.**

1. The board could not be inserted at all. The standoffs and magnet bosses now stood inside the cavity, and with the shell wrapped tightly around the board there was no way to get the PCB past them.
2. The rear openings were wrong. The RJ45 was about 2.5 mm out, the power terminal about 2.2 mm. The openings had been positioned from photographs rather than from the datasheet.
3. The 9 mm corner radius was large enough that the PCB's own corners hit the inside of the radius, pushing the board off its intended position and making the misalignment worse.

## Rev C — rebuilt from the datasheet

Everything to do with the rear face was rebuilt from Figure 4 of the Mallow V1.1 datasheet rather than from photographs. Connector centres, measured from the board's left edge:

| Connector | Centre | Width | Height |
| --- | --- | --- | --- |
| RJ45 | 14.20 | 15.74 | 13.80 |
| USB-A stack | 31.60 | 14.30 | 16.12 |
| USB-C | 48.99 | 8.92 | 3.27 |
| HDMI | 65.79 | 15.00 | 6.28 |
| Power terminal | 85.29 | 17.30 | 7.00 |

The box grew to 119 mm wide so that four corner posts could live in 7 mm side gaps **outside** the board footprint. The board footprint became clear from above: the board drops in from the top with nothing in its way. Corner radius came down to 6.5 mm. The rear wall was cut away behind the board edge so the PCB reaches the outer face.

Two decisions were forced by geometry rather than chosen:

- **Depth 76 → 79 mm.** With the board's rear edge flush, the rear panel overhangs the board's last 2.5 mm, so the board has to drop in slightly forward and slide back under the panel. At 76 mm there was no room for that movement.
- **Two front M3s instead of four.** The rear mounting holes sit 3 mm from the flush rear face. A Ø7 screw boss there breaks out through the rear panel. The rear edge rests on two plain pads and is captured under the panel instead.

## Rev D — the current design

Two corrections to rev C, both from inspection:

1. Two of the base plate's standoffs had been generated without their bores. Fixed.
2. The PCB edge was visible through the rear openings. The rear panel was thinned to 1.5 mm and the board pushed further back so the panel covers the PCB line: USB-C sits 0.3 mm inside the outer face, HDMI 0.8, USB-A 1.8, while the RJ45 and the power terminal stand 0.7 mm proud.

Also in rev D: front-face windows for the two switches (Ø4) and two LEDs (Ø2), Ø2.8 pilot bores for M3 self-tappers, Ø5.2 magnet pockets, counterbored screw holes so the base sits flat, and the ribbon slot dropped since the base plate comes off anyway.

**Printed and fitted.** The board goes in and the ports line up.

## Final dimensions

| | |
| --- | --- |
| Overall | 119 × 78 × 38 mm |
| Wall | 2.5 mm, rear panel 1.5 mm |
| Corner radius | 6.5 mm outer, square bottom edge |
| Cover gap | 3.5 mm floating, magnets only |
| Corner posts | Ø8 at ±54.75, ±32 |
| Board standoffs | 10 mm, Ø7 front pair, Ø6 rear pair |
| Clearance around connectors | 0.6 mm |
| Board pocket | board plus 1 mm per side |

## What would have saved three prints

Reading the mechanical drawing before positioning anything. Revs A and B both failed on numbers that were available in the datasheet the whole time. Photographs are good enough to tell you a connector exists and useless for telling you where it is.

The second lesson is about order of assembly. Rev B was dimensionally reasonable and still unbuildable, because nobody asked how the board actually gets in. Any feature standing inside the cavity is a feature the board has to clear on its way down.

## Testing before printing the set

`src/fit-coupon.html` exists because of the above. It is about 12 g: a gauge with three magnet-pocket diameters, and one full-size corner carrying the side wall, the radius, a corner post with its bore and pocket, a standoff, and the RJ45 window. It answers the tolerance questions for the cost of a few minutes of printing.
