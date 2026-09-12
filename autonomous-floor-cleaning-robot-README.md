# Autonomous Floor Cleaning Robot

**Autonomous cleaning robot with ultrasonic obstacle avoidance and a pump-driven wet cleaning system.**

## Overview

An autonomous floor cleaning robot built on an Arduino Uno. The robot drives itself around a room using an ultrasonic sensor for obstacle detection and avoidance, while a water pump draws from an onboard jar to wet the floor as it cleans — combining autonomous navigation with an active wet-cleaning mechanism, rather than just dry sweeping.

## Hardware

- **Arduino Uno** — main controller
- **4x DC motors** — drive system (independent wheel control for movement and turning)
- **Ultrasonic sensor (HC-SR04)** — obstacle detection and avoidance
- **Water pump** — dispenses water from an onboard jar/reservoir onto the floor during cleaning
- **Water jar/reservoir** — water supply for the pump
- **Motor driver module** (e.g. L298N) — drives the 4 motors from the Arduino's logic-level outputs
- Chassis + cleaning attachment (mop/brush)
- Battery pack

## How It Works

1. The ultrasonic sensor continuously measures distance to obstacles ahead.
2. Based on the distance reading, the Arduino decides to continue forward, turn, or reverse — driving the 4 motors through the motor driver to navigate around obstacles autonomously.
3. While moving, the pump is triggered to draw water from the jar and dispense it onto the floor, wetting the surface for the cleaning attachment to mop.
4. The robot repeats this obstacle-avoidance loop continuously, covering the room without manual steering.

## Getting Started

### Prerequisites

- Arduino IDE

### Wiring (adjust pins to match your build)

| Component | Arduino Pin |
|---|---|
| Ultrasonic Trig | e.g. D9 |
| Ultrasonic Echo | e.g. D10 |
| Motor Driver (Motors 1–4) | via motor driver module inputs |
| Pump (via relay/transistor) | e.g. D8 |

### Firmware Setup

1. Open the project's `.ino` file in the Arduino IDE.
2. Adjust pin definitions to match your wiring.
3. Tune the obstacle-avoidance distance threshold for your room size and sensor placement.
4. Upload to the Arduino Uno.

### Running It

Power on the robot. It will begin driving forward, using the ultrasonic sensor to detect obstacles and turn away from them, while the pump wets the floor as it moves.

## Design Notes

Kept deliberately simple: a single ultrasonic sensor for obstacle avoidance and straightforward motor logic, rather than mapping or path planning — prioritizing a robot that reliably avoids walls and furniture and actually cleans, over more complex navigation that's harder to get right on an Arduino Uno.

## License

MIT
