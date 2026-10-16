# Open-Source Chemical Reactor

A modular chemical reactor built on an Ender 3 gantry. Magnetic 25 mm cubes snap
together into reaction setups — spring-loaded pogo pins carry power and signal,
genderless spring-loaded fluid connectors (O-ring sealed) carry the chemistry.
Fluids in, product out, byproducts sorted. Design a new cube, share the file,
remix the chemistry.

## How it works

- **Cubes** are the unit of chemistry. Each 25 mm cube does one job: move, mix,
  heat, cool, sense, filter, or vent.
- **The gantry** is an Ender 3 motion system with a 200 mm work volume — an
  8×8 grid of cube slots. It places cubes, connects fluid/electrical lines, and
  runs the sequence.
- **Interconnects** are all spring-loaded: pogo pins for electronics, O-ring
  face seals for fluids. Cubes self-align on magnets, so the gantry just drops
  them in.

## Cube catalog

| Cube | Job |
|---|---|
| Straight | Pass-through channel |
| Elbow | 90° turn |
| T-Mixer | Two inlets merge into one outlet |
| Inlet / Outlet | Fluid enters or leaves the setup |
| Delay | Zigzag channel — residence time without extra footprint |
| Mixer | Herringbone / tortuous geometry for chaotic mixing |
| Heater | Thermal block, looped channel for max contact |
| Photochemical | Internal LEDs drive light-driven reactions |
| Peltier | Rapid heating/cooling — thermal-shock crystallization |
| Sensor | Temperature, pH, or other probes in the flow path |
| Bubbler | Gas sparging through liquid |
| Gravity chimney | Gas vents up and out, liquid stays down |
| Filtration | Filter membrane with filtrate routed to waste |
| Plug | Blank — caps an unused port |

Got an idea for a new cube? That's the point — model it, print it, share it.

## Materials

- **Wetted path:** PTFE — nothing sticks, nearly nothing reacts
- **Structure:** transparent PETG — watch the chemistry happen
- **Energy blocks** (heaters, Peltiers): aluminum or brass
- **Gaskets:** EPDM

## Gantry layout

| Zone | Location |
|---|---|
| Liquid input ×2 | Top of gantry |
| Product output | Corner |
| Discharge / waste | Corner(s) |
| Gas vacuum waste | Dedicated port |
| Pressurized N₂ or air | Optional source |

## Example run: silver precipitation

Ag + 2 HNO₃ → AgNO₃ + NO₂↑ + H₂O

1. Silver and nitric acid meet in a **T-mixer** cube
2. Through a **heater** cube (looped channel)
3. **Gravity chimney** vents NO₂ to vacuum waste
4. **Peltier** cube crash-cools → thermal-shock crystallization
5. **Filtration** cube catches crystals, filtrate goes to waste
6. Wash cycle: nitric acid flush + nitrogen purge
7. Pull the filtration cube (there's your product), cap the line to waste
8. Swap the mixer inlet for **wash manifold** cubes — flush water/nitric to
   waste, dry with nitrogen
9. Inject hot water, route through a **T**: pressurized air pushes the slurry
   out through an **L** to the output
10. Dry with heater or gas — done

## Roadmap

- [ ] Cube interconnect CAD: magnet pockets, pogo-pin seats, O-ring glands
- [ ] First cube set: straight, elbow, T-mixer, inlet/outlet, plug
- [ ] Ender 3 gantry adapter plate
- [ ] Heater + Peltier cubes
- [ ] Sensor cube (temp / pH)
- [ ] End-to-end demo: silver precipitation

## Contributing

Open an issue with your cube idea or reaction sequence. PRs with STEP/STL
files and a row for the catalog table are welcome. Keep the 25 mm grid and the
connector spec sacred — everything else is fair game.

## Safety

⚠️ This is real chemistry. Concentrated nitric acid burns, NO₂ is toxic, and
pressurized gas is unforgiving. Fume hood, PPE, and ventilation are mandatory.
Validate material compatibility before running anything — this repo is a
concept until the hardware is proven.

## License

TBD — proposed: CERN-OHL-S for hardware, MIT for software/firmware.
