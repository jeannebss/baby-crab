# Bill of Materials

**Status values:** `to buy` · `ordered` · `received` · `in use` · `spare`
**Prices:** CHF, estimates. Prices marked *(SPH)* come from the ETH Student Project House makerspace shop (checked November 2026); online prices are approximate and should be checked before ordering.
**Version:** the first version that needs the part (v1 desk companion, v2 floor exploration, v3 vision-guided grasping, v4 autonomous docking).

**Buy once:** this list is the final crab, so no part has to be replaced along the way. The body is designed from the start around the final battery, sensors, claws, speaker and dock contacts. Parts can still be bought when their version comes (see [When to buy](#when-to-buy)).

Planned build: crab-style hexapod, **6 legs × 3 DOF (18 servos) + 2 claws × 2 DOF (4 servos) = 22 servos**. The leg count is not final (4 to 6 legs, 6 targeted): quantities below are for 6 legs.

## Budget

| Version | Adds | Cost added | Total so far |
|---|---|---|---|
| **v1: desk companion** | Legs, claws (grip), brain, servo drivers, IMU, edge sensors, I²C multiplexer, eyes, speaker (voice), battery and power | 151–216 | **~150–215** |
| **v2: floor exploration** | 5 MP camera, 2 more cells, obstacle sensors, USB-C charging | 36–54 | **~185–270** |
| **v3: grasping** | Wrist servos, contact sensors, claw distance sensor, new claws | 21–38 | **~170–255** with v1 only |
| **v4: autonomous docking** | Charging dock with its own charger, spring contacts, alignment magnets, AprilTag | 12–22 | **~165–240** with v1 only |
| **Everything** | | | **~220–330** |

v2, v3 and v4 are **independent add-ons**: each one only needs v1, so they can be built in any order, or skipped.

| Group | Planned | Spent so far |
|---|---|---|
| Actuators | 63–81 | |
| Control, sensors and sound | 74–101 | |
| Power | 56–91 | |
| Dock | 12–22 | |
| Hardware and printing | 0–10 | |
| Shipping and contingency | 15–25 | |
| **Total** | **~220–330** | |

**Main budget risk: weight.** The final crab carries 4 cells, 4 metal-gear claw servos, a speaker and more sensors. The full final mass goes into MuJoCo from day one. If the MG90S don't hold it with margin, the 18 leg servos change to a stronger micro servo *before* buying them: roughly +50–100 CHF.

## Actuators

| Ref | Part | Qty | Version | Role | Source | Est. total | Status | Notes |
|---|---|---|---|---|---|---|---|---|
| A1 | Micro servo MG90S, metal gears | 21 (18 + 3 spares) | v1 | Leg joints (hip, shoulder, knee) | Online | 53–67 | to buy | Buy all from the same batch, only after the leg passes the simulation |
| A2 | Micro servo MG90S, metal gears | 2 | v1 | Claw grip (open/close): expressions in v1, grasping in v3 | Online | 5–7 | to buy | Same batch as A1. Metal gears so they can hold objects in v3 |
| A3 | Micro servo MG90S, metal gears | 2 | v3 | Claw wrist (tilt) | Online | 5–7 | to buy | Mounting points planned in the v1 claw design |

## Control, sensors and sound

| Ref | Part | Qty | Version | Role | Source | Est. total | Status | Notes |
|---|---|---|---|---|---|---|---|---|
| C1 | Seeed XIAO ESP32-S3 Sense | 1 | v1 | Microcontroller + camera + microphone (Wi-Fi, BLE) | Online | 15–18 | to buy | Real-time control, kinematics, Wi-Fi video. Comes with a 2 MP OV2640 camera (enough for v1) and a digital microphone (voice commands, optional) |
| C2 | OV5640 camera module for the XIAO Sense | 1 | v2 | Sharper image for SLAM and spotting objects | Online | 10–15 | to buy | Check compatibility with the XIAO Sense connector before ordering |
| C3 | PCA9685 16-channel servo driver | 2 | v1 | Drive the 22 servos over I²C (32 channels) | Online | 6–10 | to buy | Solder the A0 jumper on one board (addresses 0x40 and 0x41). Capacitor on each servo power input |
| C4 | IMU MPU6050 | 1 | v1 | Fall detection, tilt while walking | SPH | 2 (SPH) | to buy | |
| C5 | VL53L0X time-of-flight sensor | 2 | v1 | Desk-edge detection, pointing down on each side | SPH | 8 (4.00 each, SPH) | to buy | All VL53L0X share the same I²C address: each one goes on its own port of the multiplexer (C8) |
| C6 | VL53L0X time-of-flight sensor | 2 | v2 | Obstacles ahead when walking on the floor | SPH | 8 (4.00 each, SPH) | to buy | |
| C7 | VL53L0X time-of-flight sensor | 1 | v3 | Distance to the object between the claws | SPH | 4 (SPH) | to buy | |
| C8 | TCA9548A I²C multiplexer | 1 | v1 | Connects up to 8 VL53L0X on 2 wires | Online | ~3 | to buy | In v1 so the v2 and v3 sensors just plug in, in any order. Saves GPIO: the XIAO only has 11 |
| C9 | OLED display 128×64 | 1 | v1 | Expressive eyes | SPH | 3 (SPH) | to buy | |
| C10 | MAX98357A I²S amplifier | 1 | v1 | Drives the speaker | Online | 3–6 | to buy | 3 GPIO (BCLK, LRC, DIN). Powered from the 5 V logic rail |
| C11 | Small speaker, 8 Ω, 1–2 W (~20–28 mm) | 1 | v1 | Voice ("Work!"), sounds, beeps | Online or SPH | 2–4 | to buy | Replaces the buzzer. Grille in the shell, facing forward |
| C12 | Force-sensitive resistor (FSR), small | 2 | v3 | Contact sensing inside the claws | Online | 10–20 | to buy | Analog inputs on the XIAO: use ADC1 pins (A0–A3), ADC2 does not work while Wi-Fi is on |

**XIAO pin budget (11 GPIO):** I²C 2 (servo drivers, IMU, multiplexer, OLED) · I²S speaker 3 · battery voltage 1 · FSR 2 · 3 free. The camera and microphone use their own pins on the Sense board.

## Power

| Ref | Part | Qty | Version | Role | Source | Est. total | Status | Notes |
|---|---|---|---|---|---|---|---|---|
| P1 | 18650 Li-ion cell, branded, high-drain (≥ 10 A) | 2 | v1 | Onboard battery (2S) | Local electronics shop | 10–16 | to buy | ~3000 mAh each. Avoid unbranded cells. All 4 cells from the same model and batch |
| P2 | 18650 Li-ion cell, same model as P1 | 2 | v2 | Second parallel pair (2S2P): double battery life | Local electronics shop | 10–16 | to buy | Never mix used and new cells: buy all 4 at once if the 2S2P pack is used from v1 |
| P3 | 2S2P holder + 2S BMS (≥ 15 A) | 1 | v1 | Cell protection, sized for the final pack | Online | 5–8 | to buy | Works with 2 cells in v1 (2S1P) if needed. Check the current rating against the measured servo peaks |
| P4 | 18650 charger | 1 | v1 | Charging | Online | 8–12 | to buy | Skip if you already have one |
| P5 | Step-down converter, 8–10 A | 2 | v1 | Servo rails, one per PCA9685 | Online | 12–20 | to buy | 22 servos can peak well above 10 A together |
| P6 | Adjustable step-down DC-DC, 3 A | 1 | v1 | 5 V logic rail: ESP32 and speaker amplifier | SPH | 1 (SPH) | to buy | Separate rail so servo current peaks do not reset the ESP32 |
| P7 | XT30 connectors, main switch, capacitors, wires | 1 lot | v1 | Battery connector, main switch, wiring | SPH | 5–8 | to buy | XT30 0.50 each, switch 0.30 (SPH). The main switch is mandatory; check its current rating |
| P8 | Resistor divider (2 resistors) | 1 | v1 | Battery voltage measurement on an ADC1 pin | SPH | ~0 | to buy | Lets the crab know its battery level; needed for docking in v4 |
| P9 | USB-C 2S charging module | 1 | v2 | Charge without removing the cells | Online | 5–10 | to buy | Space for it planned in the shell from v1. Use only one charger at a time (this one or the dock) |

## Dock (v4)

| Ref | Part | Qty | Version | Role | Source | Est. total | Status | Notes |
|---|---|---|---|---|---|---|---|---|
| D1 | USB-C 2S charging module | 1 | v4 | Charger inside the dock | Online | 5–10 | to buy | In the dock, so v4 does not need the v2 onboard charger |
| D2 | Spring-loaded pogo pins + contact pads | 2 pairs | v4 | Charging contacts (pins on the dock, pads under the crab's belly) | Online | 3–5 | to buy | Pad positions planned in the v1 shell |
| D3 | Small neodymium magnets | 4 | v4 | Pull the crab into position on the contacts | Online or SPH | 2–3 | to buy | Keep them away from the IMU |
| D4 | USB-C cable / connector, wires | 1 lot | v4 | Dock power | SPH | 2–4 | to buy | |
| D5 | AprilTag | 1 | v4 | Marker the crab steers towards | Printed on paper | 0 | | |

## Hardware and printing

| Ref | Part | Qty | Version | Role | Source | Est. total | Status | Notes |
|---|---|---|---|---|---|---|---|---|
| M1 | M2 and M3 nuts, M3 screws | as needed | v1 | Assembly | SPH | 0 (SPH) | | |
| M2 | Servo horns and screws | | v1 | Leg and claw joints | Included with servos | 0 | | |
| F1 | PETG filament | | v1 | Legs, feet, claws, chassis: parts under load or near heat | SPH | 0–10 | | Tougher and less brittle than PLA, holds ~80 °C (battery, converters, warm servos). Weight per part to fill in below |
| F2 | PLA filament | | v1 | Lid, head, dock, test prints | SPH | incl. above | | Easier to print, more precise, stiffer. Fine for parts without load |
| F3 | Silicone bumper feet (self-adhesive) or rubber caps | 6 (+ spares) | v1 | Grip under each foot | Online or hardware store | 3–6 | to buy | No TPU printer: grip goes on as a replaceable tip, in a small pocket at the end of each foot. Covered by the contingency line |
| F4 | Rubber pads or grip tape | 1 lot | v3 | Grip inside the claws | Online or hardware store | ~2 | to buy | Glued into a pocket on the v3 claws |

## Printed parts

| Ref | Part | Qty | Version | Material | Weight (g) | Status | Notes |
|---|---|---|---|---|---|---|---|
| 3D1 | Single 3-DOF leg (test) | 1 | v1 | PLA first, then PETG | | | Phase 1, after validation in MuJoCo. PLA for fit tests, PETG for the real one |
| 3D2 | Leg set | 6 | v1 | PETG | | | Add printed end stops if servo backlash makes the legs shake |
| 3D3 | Feet | 6 | v1 | PETG + rubber tip (F3) | | | Pocket for the bumper foot |
| 3D4 | Body shell: chassis + lid | 1 | v1 | Chassis PETG, lid PLA | | | Designed for the final layout: 2S2P pack, 2 PCA9685, multiplexer, 5 sensor mounts, speaker grille, USB-C module space, dock contact pads and magnets under the belly |
| 3D5 | Head / camera mount | 1 | v1 | PLA | | | Fits both the OV2640 and the OV5640. Camera tilted up; final angle after testing |
| 3D6 | Claws (v1) | 2 | v1 | PETG | | | Grip servo + mounting points for the v3 wrist servo |
| 3D7 | Claws (v3) | 2 | v3 | PETG + rubber pads (F4) | | | Wrist, FSR pockets, distance sensor mount, pad pockets |
| 3D8 | Charging dock | 1 | v4 | PLA | | | Ramp or guides so the crab lines up, AprilTag holder, pogo pins, magnets |

## When to buy

1. **Now (not affected by the simulation):** ESP32-S3 Sense, 2 × PCA9685, IMU, 2 edge sensors, I²C multiplexer, OLED, amplifier + speaker, power parts (P1, P3–P8).
2. **After the leg passes the simulation:** the 25 MG90S (A1–A3), all from one batch.
3. **Before v2:** C2, C6, P2, P9. **Before v3:** A3, C7, C12. **Before v4:** D1–D5. Already designed in, so nothing else changes.

## Independent add-ons

v2, v3 and v4 are independent add-ons: each one only needs v1, so they can be built in any order, or skipped. What keeps them independent:
- the I²C multiplexer is in v1, so any distance sensor plugs into a free port
- 32 servo channels for 22 servos, so the wrist servos have their place
- the stock camera is enough for grasping nearby objects and reading the dock's AprilTag; the v2 camera only improves it
- the dock has its own charger, and the battery voltage divider is in v1
- the simulation is checked with the heaviest combination (all add-ons), so the legs hold any combination

## Saving money

- Group all online orders into one to pay shipping once.
- Reuse or borrow an 18650 charger.
- Try a leg with SG90 servos first (2 CHF each, SPH): if they hold the hips, that is 6 fewer MG90S.
- Buy each version's parts only when that version starts.

## Possible upgrades

1. Serial-bus servos with position feedback, for closed-loop control
2. Bigger screen

## Lessons

Things worth knowing before buying (filled in as the build progresses).
