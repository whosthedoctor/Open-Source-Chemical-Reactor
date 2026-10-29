# Magnet head + cube face layout

Face template updated to the square 4/7 layout (Oct 2026): corner magnets/steel 4 mm from all edges, pogo pins/pads 7 mm from all edges, to centres. The diagram `docs/cube-face-template-gasket.png` shows the same layout.

Decision: plain permanent-magnet head, no gripper fingers, no electromagnet.
The two NEMA11s (rotation + lift) are reused; nothing new is motorised.

## The head (all printed except the magnet)

- **Cup**: printed PETG cup on the rotation axis, press-fit magnet + retaining
  lip (or a drop of glue). No fingers, no jaws, no linkages.
- **Head magnet**: one Ø14 × 3 mm disc magnet (N52-grade equivalent) in the
  cup. Pulls the cube's top steel disc with kilograms of force; a cube
  weighs tens of grams, so hold is not marginal.
- **Stripper ring (recommended, passive)**: a fixed plate on the carriage
  with a hole bigger than the head but smaller than the cube. To release,
  the head retracts up through it and the plate knocks the cube off. No
  actuator, no wiring. Only needed if a cube ever sticks to the head.
- **Pick / place sequence** (what the PICK_CUBE macro will do once the
  geometry is final): lower head onto cube → lift → move → rotate to
  orient ports → lower into slot → lift away. The grid's side magnets
  hold the cube in place while the head leaves.

## Why the pickup target is steel, not a magnet

If both head and cube top were magnets, half of all cube orientations
would repel instead of attracting (polarity flips with rotation). Steel
is attracted no matter the polarity, so pickup works in every orientation.
Rule: **magnet on the head, steel on the cube** — never magnet-on-magnet
for pickup.

## Cube face template (25 × 25 mm faces)

Coordinates in mm from the face centre, viewed from outside the cube,
+up toward the cube top. Every side face uses the SAME template, so any
cube can sit in any orientation.

| Feature | Position | Size | Notes |
|---|---|---|---|
| Fluid port | centre (0, 0) | Ø10 seal zone, Ø4 bore | Centre placement is rotation-proof: the port lines up no matter how the cube is turned. Loose FKM O-ring face seal (5 × 1.5 mm, one per mated pair, groove ID Ø5.5 / OD Ø9.5, 0.6 mm deep per face) + the existing genderless connector concept. |
| Pogo pins | (−5.5, +5.5), (+5.5, −5.5) | Ø2 | Spring pins, 7 mm from all edges to centres. |
| Pads | (+5.5, +5.5), (−5.5, −5.5) | Ø2 flat pads | Mating faces' pins land here, 7 mm from all edges to centres. |
| Snap magnets | (−8.5, +8.5), (+8.5, −8.5) | Ø4 × 3 mm | Diagonal pair, 4 mm from all edges to centres. |
| Snap steel discs | (+8.5, +8.5), (−8.5, −8.5) | Ø4 × 1.5 mm | Diagonal pair, opposite corners from the magnets, 4 mm from all edges to centres. |

### Why diagonal magnet/steel (and diagonal pin/pad)

Two cubes meeting side by side are mirror images of each other; a cube
placed rotated 180° meets rotated. The diagonal arrangement maps magnets
onto steel and pins onto pads under BOTH mirror and 180° rotation, so
every magnet lands on steel and every pin lands on a pad no matter which
way the cube is turned. No orientation bookkeeping, no polarity mistakes.

### Circuits

One mated face pair gives 4 conducting paths (my 2 pins → neighbour's
2 pads, neighbour's 2 pins → my 2 pads). Suggested assignment: 24 V, GND,
signal A, signal B. Heater cubes use 24 V + GND + NTC signal; sensor
cubes use power + signal lines. Each cube's internal wiring taps the same
4-wire bus in the same pattern on every face — that internal routing is
part of cube CAD, not the head design.

### Clearances (tolerance watch)

- Magnet pocket edge to pogo hole edge: ~1.2 mm. Magnet pocket to face
  edge: 2.0 mm wall (Ø4 pocket centred at ±8.5 leaves 10.5 mm, face ends
  at 12.5 mm).
- Fluid seal zone (Ø10) clears the electrical contacts by ~1.8 mm
  (pin edge to seal-zone edge). Tightest wall overall is the 0.5 mm
  between adjacent-face magnet and steel pockets (pocket extents, not
  centreline distance) — a test face print is advised before committing
  to a full run of cubes. Nothing overlaps.

## Top and bottom faces

- **Top face**: one steel disc, Ø12 × 1.5 mm, centred, recessed flush.
  Nothing else on the top face — it is the pickup face only.
- **Bottom face**: plain. It sits in a pocket of the staging/grid tray.
- **Tray**: printed pocket tray, NON-magnetic. The bed must not hold the
  cubes magnetically or pickup fights hold-down. Grid hold comes from
  the side-face magnets between neighbouring cubes, and edge slots get
  their hold from the pocket walls.

## What changes elsewhere

- **BOM**: purely additive (see below). No gripper parts were ever in the
  BOM — the fingers were CAD-only, printed from the PETG already listed.
- **Config**: no pin changes. Rotation + lift axes stay; only the header
  comments and the PICK_CUBE description change to the magnet head.
- **Wiring diagram**: only the motion labels change
  ("Grabber rotation/lift" → "Magnet head rotation/lift").
- **Cube CAD (John's work)**: finger assembly is deleted; replaced by the
  magnet cup + stripper ring, corner pockets (Ø4 magnets + Ø4 steel),
  top steel recess (Ø12), and the face template above.

## BOM delta

| Part | Qty | Price | Notes |
|---|---|---|---|
| Head magnet, Ø14 × 3 mm disc (pack of 20) | 1 pack | $16.99 | 1 needed, 19 spares |
| Corner magnets, Ø4 × 3 mm (pack of 100) | 1 pack | $16.99 | 2 per cube → 40 for 20 cubes + spares |
| Cube-top steel discs, Ø12 × 1.5 mm (pack of 20) | 1 pack | $9.00 | Estimate — verify; 1 per cube |
| Corner steel discs, Ø4 × 1.5 mm (pack of 100) | 1 pack | $8.00 | Estimate — verify; 2 per cube |

Delta: +$50.98 → new BOM total $565.09 (was $514.11).

## Open for cube CAD (not decided here)

- Magnet pocket depth + glue vs press-fit; steel recess depth (flush).
- Tray pocket size (cube + clearance) and pocket wall height.
- Whether edge slots need anything extra for hold (pocket walls should
  be enough; revisit if cubes walk during gantry moves).
