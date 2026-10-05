# Open-Source-Chemical-Reactor
I want to build a modular chemical reactor using an Ender 3 gantry system that arranges magnetic cubes with pogo connectors into a reaction setup, takes fluids as inputs, produces an output, and sorts byproducts, with an open-source ability to make new cubes or cutting-edge technology cubes.

The pogo connectors are spring-loaded, and the fluid connections are also spring-loaded with O-rings and genderless. Decent idea, I believe. An Ender 3 could move in a 200 mm cube, so cubes should be 25 mm sized.

Different types of cubes: straight, elbow, T Mixer, Outlet/Inlet Cube, Delay Cube (basically a zigzag), Mixer Cube (herringbone/tortuous geometry), thermal heating cube, photochemical reactor cube with internal LEDs, Peltier cube, sensor cube, bubbler cube, gravity chimney, plug cube, filtration cube.

Cubes should be made of internal PTFE, structurally out of transparent PETG, energy blocks made of aluminum or brass, and gaskets should be made of EPDM.

Areas or Parts of the Gantry: One output area in a corner, two LIQUID input areas at the top of the gantry system, and discharge/waste in another corner(s) + gas vacuum waste, a possible pressurized nitrogen or air source.

For example, for silver precipitation:
 - Ag + HNO_3 -> AgNO_3 + NO_2 + H_2O
 - AG and HNO_3 are mixed in a Y, and then passed into a Heater, passing through a loop in the heater, then pass through a chimney to the vacuum waste, and then the solution passes through a Peltier where it crystallizes from thermal shock, passes into filtration cube connected to waste, washes the whole thing with nitric acid and nitrogen, takes away filtration cube + product and connects the end to the waste, and then replaces the input lines with wash manifold cubes in the mixer inlet, takes away the product, washes out the reaction setup with water and nitric into waste, and/or flushes with nitrogen gas to dry, and injects a small amount of hot water, and then connects it to a T, input to the pressurized air source and output, and the other one to an L, opens the valve, pushes the slurry through, output goes out of the L, and then connects the air to the L, pushes the slurry into the output, and then dries it with a heater or gas.
