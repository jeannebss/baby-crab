# Bill of Materials

**Status values:** `to buy` · `ordered` · `received` · `in use` · `spare`
**Prices:** CHF. Prices marked *SPH* were seen on the SPH Materials Shop.

## Budget tracker

| Step | Planned | Spent so far |
|---|---|---|
| 1. Sesame (8 servos) | ~35 to 55 | |
| 2. Single-leg test bench | ~3 | |
| 3. Sesame+ (12 servos) | ~25 to 40 | |
| 5. Vision (phone or ESP32-CAM) | 0 to 10 | |
| **Total** | **~60 to 100** | |

## Actuators

| Ref | Part | Qty | Role | Where to buy | Unit price | Status | Notes |
|---|---|---|---|---|---|---|---|
| A1 | Micro servo SG90, 9 g | 3 (test leg), up to 12 | Leg joints | SPH Materials Shop, ref [L01] | 2.00 (SPH) | to buy | Plastic gears. Check the Sesame BOM: it specifies MG90 servos |
| A2 | Micro servo MG90S (metal gears) | | Leg joints, if SG90 wears out | TODO | ~3 to 4 | | |

## Control and electronics

| Ref | Part | Qty | Role | Where to buy | Unit price | Status | Notes |
|---|---|---|---|---|---|---|---|
| C1 | ESP32 board (Lolin S2 Mini recommended by Sesame) | 1 | Microcontroller | TODO | ~5 to 8 | to buy | Check the model in the Sesame BOM |
| C2 | OLED display 0.96" (optional) | 1 | Face / status | TODO | ~3 to 4 | | Only if building Sesame as designed |
| C3 | IMU (e.g. MPU6050) | 1 | Body orientation | TODO | ~2 to 4 | | Step 3 / 4 |
| C4 | PCA9685 servo driver (optional) | 1 | More servo channels | TODO | ~4 | | Only if the ESP32 lacks enough pins |
| C5 | Protoboard ~5 x 7 cm | 1 | Power and signal distribution | SPH (check Prototype Boards) | | | |

## Power

| Ref | Part | Qty | Role | Where to buy | Unit price | Status | Notes |
|---|---|---|---|---|---|---|---|
| P1 | Adjustable step-down DC-DC converter, 3 A | 1 to 2 | 5 V rail for servos | SPH, ref [E15] | 1.00 (SPH) | to buy | Two converters can share the load of 12 servos |
| P2 | Banana plug cable, 1 m | 1 | Bench supply to robot | SPH, ref [F19] | 2.00 (SPH) | to buy | |
| P3 | Alligator clip cable, 50 cm | 2 | Bench supply to robot | SPH, ref [F20] | 0.65 (SPH) | to buy | |
| P4 | Capacitor(s) for servo power rail | | Smooth current spikes | SPH (Capacitor category) | | | Value to decide, check the Sesame wiring guide |
| P5 | Silicone wire, 22 AWG | | Power and ground lines | TODO | | | |
| P6 | Battery (2S Li-ion) with protection and charger | | Wireless operation | TODO | ~15 to 30 | later | Not before the robot walks on the bench supply |

## Mechanical and hardware

| Ref | Part | Qty | Role | Where to buy | Unit price | Status | Notes |
|---|---|---|---|---|---|---|---|
| M1 | Screws, nuts, washers (sizes from the Sesame BOM) | | Assembly | SPH (free, according to what you told me) | 0 | | Note the exact sizes here |
| M2 | Servo horns and screws | | Included with servos | | | | |

## Printed parts

SPH charges 0.05 CHF/g for PLA (SPH).

| Ref | Part | Qty | Weight (g) | Cost | Status | Notes |
|---|---|---|---|---|---|---|
| 3D1 | Servo bracket test | 1 | | | | First print, to check the fit |
| 3D2 | Sesame body and legs | 1 set | | ~4 to 6 | | |
| 3D3 | Sesame+ body and legs | 1 set | | ~10 to 15 | | |

## Free tools at SPH (not bought)

Soldering station, bench power supply, multimeter, oscilloscope, hand tools, 3D printers.

## Lessons

To note things I wish I had known before buying.

- TODO