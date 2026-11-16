# Baby-crab
> diving into the robotic world with a cute crab :P

A solo, from-scratch legged robot project: I design, print, wire, program and test everything myself, starting from the open-source [Sesame robot](https://github.com/dorianborian/sesame-robot) and extending it step by step (8 servos, then 12 servos with 3-DOF legs, then sensors and visual SLAM).

## Status

- **Current stage:** Step 0 (setup and CAD basics)
- **Last update:** 2026-11-16
- **Robot walks?** Not yet

## Goals

- Learn parametric CAD and design for 3D printing
- Learn servo electronics, power distribution and embedded firmware
- Derive and implement leg inverse kinematics myself
- Implement gaits (crawl, then trot) and use an IMU
- Add perception: visual odometry, then SLAM

## Roadmap

- [ ] **Step 0:** Tools set up (Onshape, Git, Python), first printed part that fits a servo
- [ ] **Step 1:** Build Sesame (8 servos) and understand every wire and main function of the firmware
- [ ] **Step 2:** One 3-DOF leg on the bench, inverse kinematics in Python then on the microcontroller (foot within ±5 mm of target)
- [ ] **Step 3:** Sesame+ with 12 servos: redesigned body and legs, stronger power supply
- [ ] **Step 4:** Gaits and IMU (walks 1 m straight without falling)
- [ ] **Step 5:** Perception: phone or small camera, visual odometry, then visual SLAM
- [ ] **Step 6:** Upgrades (battery, onboard computer, 6 legs, serial-bus servos), if I want them

## Repository structure

```
cad/        CAD exports (STEP/STL) and links to the Onshape documents
firmware/   Code running on the microcontroller
sim/        Python notebooks: kinematics, plots, tests
docs/       Bill of materials, wiring diagrams, photos
journal.md  Milestone log: key progress, lessons and design decisions
```

## Bill of materials

See [docs/bom.md](docs/bom.md): quantity, role, where to buy, price and status for each part.

## Getting started

### Python environment (kinematics and simulation)

Windows (PowerShell):

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install numpy matplotlib jupyter
```

macOS / Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install numpy matplotlib jupyter
```

### Firmware

Not started yet. Planned toolchain: Arduino IDE (same as Sesame), on an ESP32 board.
Flashing instructions will be added during Step 1.

### Power

Development is done on a bench power supply (SPH Makerspace), not on batteries.
Planned settings: 5.0 V, current limit around 1 A for a single leg and 2 to 3 A for the full robot.
Connection details and wiring diagram will be added once validated.

## Results

No results yet. This section will fill up as each step is completed (photos, GIFs, plots).

## Credits and licenses

- Parts of this project are derived from the **Sesame Robot** by Dorian Todd (https://github.com/dorianborian/sesame-robot), released under the Apache License 2.0. Modified files carry a notice at the top, and larger design changes are described in the project journal.
- Original work in this repository (own leg design, inverse kinematics, gaits, perception code) is also released under the Apache License 2.0. See [LICENSE](LICENSE).

## Build log

See [journal.md](journal.md).
