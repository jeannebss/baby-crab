# Baby-crab
> diving into the robotic world with a cute crab :P

A low-cost, open-source legged crab robot that I design, 3D print, wire and program myself, to learn robotics end to end. Once it walks, it moves onto my desk as a camera-based focus companion.

## Status

- **Current phase:** 0–1 (tools, first 3-DOF leg in CAD, inverse kinematics in Python)
- **Robot walks?** Not yet

## The crab

- **Body:** a crab-style hexapod. 4 to 6 legs, 6 targeted, each with 3 joints (hip, shoulder, knee), plus 2 front claws with 1 servo each, and a wrist servo each added in v3. That's 22 servos with 6 legs.
- **Brain:** Seeed XIAO ESP32-S3 Sense (Wi-Fi, BLE, camera) handles real-time control.
- **Heavy lifting:** vision (OpenCV, MediaPipe, YOLO) runs on the laptop. The robot talks to it in JSON over WebSocket/UDP on Wi-Fi.

## v1: focus companion

The phone goes away, and the crab keeps an eye on the session:

- starts work sessions
- notices when I leave or pick up my phone
- reacts with its claws: waves, claps, sulks
- talks: a little "Work!" when I drift, cheers when I hold on
- celebrates breaks
- only walks over to me when something really matters

Optional: voice commands ("start session", "break") through its microphone. No image or sound ever leaves the laptop.

## Hardware (planned)

- 3-DOF legs + claw servos, driven by 2 × PCA9685
- Seeed XIAO ESP32-S3 Sense
- IMU, downward-facing distance sensors so it never walks off the desk, OLED for the eyes
- Small speaker for its voice, microphone on the XIAO
- 2S battery (2 × 18650) with BMS, main switch and step-down converters

Designed once for the final crab: v2, v3 and v4 parts are independent add-ons that plug into v1, without replacing anything. Full list and budget: [docs/bom.md](docs/bom.md).

## How it's built

Nothing gets printed before it works in simulation:

**Onshape → onshape-to-robot → MuJoCo → 3D print → real robot**

## Roadmap

- [ ] **v1: desk companion**
  - [ ] Tools, first 3-DOF leg in CAD, inverse kinematics
  - [ ] Leg checked in MuJoCo, then one real leg
  - [ ] Full crab walking on battery
  - [ ] Vision on the laptop
  - [ ] Focus companion behaviours and voice
- [ ] **v2: floor exploration:** visual SLAM and navigation to find me in the flat
- [ ] **v3: vision-guided grasping:** the claws pick up small, light objects and bring them back
- [ ] **v4: autonomous docking:** when its battery runs low, the crab walks back to its charging dock on its own
- **Maybe later:** a bigger screen, an RL-learned gait, several crabs talking to each other

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

Firmware instructions will be added once the first real leg is built.

## Safety

The robot carries Li-ion cells: use branded, protected cells with a BMS, a main switch, and never charge unattended.

## License

Apache License 2.0. See [LICENSE](LICENSE).

Credits: the firmware architecture (embedded web server, JSON API) is inspired by the open-source Sesame robot. More credits will be added as other projects are used.
