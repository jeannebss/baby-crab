# Baby-crab
> diving into the robotic world with a cute crab :P

A low-cost, open-source walking crab robot, built from scratch to learn robotics end to end, and meant to end up as a camera-based focus companion on the desk.

The crab is a quadruped with 4 legs of 3 joints each, walking sideways, plus two servo claws for expressions (waving, clapping, sulking). It runs on its own battery; vision and behaviour run on a laptop over Wi-Fi.

## Status

- **Current phase:** Phase 0 (simulation and leg design)
- **Robot walks?** Not yet

## Goal

**Focus companion:** during work sessions, the crab notices when you pick up your phone or leave, and reacts.

It works in two modes, switchable at any time:

- **Desk mode:** sits next to your screen, stays in view, and uses its edge sensors to never walk off the desk.
- **Floor mode:** for small desks. Stays on the floor nearby, tilts its body up to look at you, and uses sounds so its reactions are noticed.

Camera images are processed on the laptop only.

## Ideas for later

Not planned yet, to be explored once the companion works:

- **Walking 3D scanner:** circle around an object, take photos, and reconstruct a 3D model on the laptop.
- **Find someone at home:** explore the floor with visual SLAM and look for a person.

## Hardware (planned)

- 12 × MG90S servos for the legs, 2 × SG90 for the claws, PCA9685 servo driver
- Seeed XIAO ESP32-S3 Sense (microcontroller + camera)
- IMU, downward-facing distance sensors to avoid falling off the desk, small OLED face, buzzer
- 2 × 18650 Li-ion cells with BMS

Full list and budget (target about 115–155 CHF): [docs/bom.md](docs/bom.md).

## Roadmap

Every leg design is checked in simulation (MuJoCo) before it is printed.

- [ ] **Phase 0:** leg kinematics and simulation
- [ ] **Phase 1:** one real leg
- [ ] **Phase 2:** full robot walking on battery
- [ ] **Phase 3:** vision
- [ ] **Phase 4:** focus companion
- [ ] **Phase 5:** documentation and release

## Repository structure

```
cad/        CAD exports (STEP/STL) and links to the Onshape documents
firmware/   Microcontroller code
sim/        Kinematics notebooks and simulation model
docs/       Bill of materials, wiring diagrams, photos
```

## Getting started

Python environment (kinematics and simulation):

```bash
python -m venv .venv
# Windows: .venv\Scripts\Activate.ps1
# macOS / Linux: source .venv/bin/activate
pip install -r requirements.txt
```

Firmware instructions will be added in Phase 1.

## Safety

The robot carries Li-ion cells: use branded, protected cells with a BMS, a main switch, and never charge unattended.

## License

Apache License 2.0. See [LICENSE](LICENSE). Credits to the projects this work builds on will be added as they are used.
