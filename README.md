# Open-Source Chemical Reactor

A modular chemical reactor built into an Ender 3 gantry. Magnetic 25 mm cubes snap
together into reaction setups — spring-loaded pogo pins carry power and signal;
genderless spring-loaded fluid connectors (O-ring sealed) carry the chemistry. Each cube is internally sealed with Teflon/PTFE.
Fluids in, product out, byproducts sorted. Design a new cube, share the file, remix the chemistry.

## Why

I built this because I wanted to do chemistry reactions.

## Uses of this machine
Students would be able to synthesize and create new chemicals without having to purchase expensive lab materials and PPE, and would not have to require a team of scientist to do the same work.
College students would be able to quickly make new chemicals and compounds without having to purchase and wait for shipping or funding -> rapid prototyping.
Industries would be able to use this to make a universal chemical creation factory, where one can order a specific chemical compound/formula, and then get it sent back or tested with the industry.




<img width="667" height="799" alt="image" src="https://github.com/user-attachments/assets/894a9ee6-4616-4a38-b1f3-864dfc8b9c59" />

**Image of the gantry on the head of where the Ender3 Extruder would be.**
## How it works

- **Cubes** are the unit of chemistry. Each 25 mm cube does one job: move, mix,
  heat, cool, sense, filter, or vent.
- **The gantry** is an Ender 3 motion system with a 200 mm work volume — an
  8×8 grid of cube slots. It places cubes, connects fluid/electrical lines, and
  runs the sequence.
- **Interconnects** are all spring-loaded: pogo pins for electronics, O-ring
  face seals for fluids. Cubes self-align on magnets, so the gantry just drops
  them in with a magnetic manipulator.

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

## License
MIT
