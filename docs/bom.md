# Bill of Materials

**Status values:** `to buy` · `ordered` · `received` · `in use` · `spare`
**Prices:** CHF, estimates. Prices marked *(SPH)* come from the ETH Student Project House makerspace shop (checked November 2026); online prices are approximate and should be checked before ordering.

Target: **about 115–155 CHF** for the full robot, under 150 CHF with the savings tips below.

## Budget tracker

| Group | Planned | Spent so far |
|---|---|---|
| Actuators | 39–49 | |
| Control and sensors | 32–37 | |
| Power | 32–50 | |
| Hardware and printing | 0–5 | |
| Shipping and contingency | 10–15 | |
| **Total** | **~115–155** | |

## Actuators

| Ref | Part | Qty | Role | Source | Est. total | Status | Notes |
|---|---|---|---|---|---|---|---|
| A1 | Micro servo MG90S, metal gears | 14 (12 + 2 spares) | Leg joints | Online | 35–45 | to buy | Buy all from the same batch to reduce backlash differences |
| A2 | Micro servo SG90, 9 g | 2 | Claws | SPH | 4 (2.00 each, SPH) | to buy | Plastic gears: fine for claws, likely too weak for femur and tibia (check in simulation) |

## Control and sensors

| Ref | Part | Qty | Role | Source | Est. total | Status | Notes |
|---|---|---|---|---|---|---|---|
| C1 | Seeed XIAO ESP32-S3 Sense | 1 | Microcontroller + camera | Online | 15–18 | to buy | Real-time control, kinematics, Wi-Fi video |
| C2 | PCA9685 16-channel servo driver | 1 | Drives the 14 servos over I²C | Online | 3–5 | to buy | Add a capacitor on its servo power input |
| C3 | IMU MPU6050 | 1 | Fall detection, tilt while walking | SPH | 2 (SPH) | to buy | |
| C4 | VL53L0X time-of-flight sensor | 2 | Desk-edge detection, pointing down on each side | SPH | 8 (4.00 each, SPH) | to buy | Same default I²C address: wire XSHUT to assign addresses at boot. Go to 4 (one per corner) if the crab also walks forwards |
| C5 | OLED display 128×64 | 1 | Expressive eyes | SPH | 3 (SPH) | to buy | |
| C6 | Buzzer (passive) | 1 | Sounds, so reactions are noticed in floor mode | SPH or online | ~1 | to buy | Price to check |

## Power

| Ref | Part | Qty | Role | Source | Est. total | Status | Notes |
|---|---|---|---|---|---|---|---|
| P1 | 18650 Li-ion cell, branded, high-drain (≥ 10 A) | 2 | Onboard battery (2S) | Local electronics shop | 10–16 | to buy | ~3000 mAh each, ~22 Wh total. Avoid unbranded cells |
| P2 | 2S holder + BMS | 1 | Cell protection | Online | 3–5 | to buy | |
| P3 | 18650 charger | 1 | Charging | Online | 8–12 | to buy | Skip if you already have one. Later: USB-C 2S charging module |
| P4 | Step-down converter, 8–10 A | 1 | Servo rail | Online | 6–10 | to buy | Alternative: two converters, each feeding half the servos |
| P5 | Adjustable step-down DC-DC, 3 A | 1 | ESP32 logic rail | SPH | 1 (SPH) | to buy | Separate rail so servo current peaks do not reset the ESP32. Not enough for the servos |
| P6 | XT30 connectors, slide switch, capacitors, wires | 1 lot | Battery connector, main switch, wiring | SPH | 4–6 | to buy | XT30 0.50 each, switch 0.30 (SPH). The main switch is mandatory |

## Hardware and printing

| Ref | Part | Qty | Role | Source | Est. total | Status | Notes |
|---|---|---|---|---|---|---|---|
| M1 | M2 and M3 nuts, M3 screws | as needed | Assembly | SPH | 0 (SPH) | | |
| M2 | Servo horns and screws | | Leg and claw joints | Included with servos | 0 | | |
| F1 | PLA filament | | Body shell, legs, printed end stops | SPH | 0–5 | | Weight per part to fill in below |
| F2 | TPU filament | | Feet | SPH | incl. above | | |

## Printed parts

| Ref | Part | Qty | Material | Weight (g) | Status | Notes |
|---|---|---|---|---|---|---|
| 3D1 | Single 3-DOF leg (test) | 1 | PLA | | | Phase 1, after validation in MuJoCo |
| 3D2 | Leg set | 4 | PLA | | | Add printed end stops if servo backlash makes the legs shake |
| 3D3 | Feet | 4 | TPU | | | |
| 3D4 | Body shell | 1 | PLA | | | Houses battery, BMS, switch, electronics, sensor mounts |
| 3D5 | Head / camera mount | 1 | PLA | | | Phase 3. Camera tilted up (~20–35°) so it can see the user from the floor too; final angle after the floor test |
| 3D6 | Claws | 2 | PLA | | | Phase 4 |

## Saving money

- Group all online orders into one to pay shipping once.
- Reuse or borrow an 18650 charger.
- Try a leg with SG90 servos first (2 CHF each): if they hold the hips, that is 4 fewer MG90S.
- Spread purchases: claw servos, the OLED and the second edge sensor are only needed in Phase 4.

## Possible upgrades

1. Spare servos
2. Serial-bus servos with position feedback, for closed-loop control
3. Better camera for the 3D scanner
4. USB-C charging module and a desk docking station

## Lessons

Things worth knowing before buying (filled in as the build progresses).
