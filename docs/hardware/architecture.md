# Huggy Gomboc — Hardware Architecture

## Overview

This document describes the planned hardware architecture of the Huggy Gomboc project. It focuses on the physical systems (sensors, controllers, power, displays, sound, and movement) and the staged approach for development from simple reactions to advanced humanoid movement.

## Core Principle

The physical system follows a simple robotics loop:

INPUT → STATE / COMMAND → OUTPUT

Examples:

- touch → SAFE state → eyes close + slow heartbeat
- touch → SHY state → pink heartbeat + small head turn
- distance detected → ATTENTION state → face looks toward the user
- AI command → COMFORT state → arms open + soft voice

## Controller Layers

We separate control into two layers:

1. Low-level physical controller
   - Candidates: ESP8266 (prototype), ESP32 / ESP32-S3 (later)
   - Responsibilities:
     - Read touch and other low-level sensors
     - Control LED heartbeat, display face, servos/motors
     - Run safe predefined movement sequences
     - React quickly even if the AI system is unavailable

2. High-level computer
   - Candidates: laptop (development), Raspberry Pi (standalone), Jetson (advanced vision)
   - Responsibilities:
     - Microphone and speaker handling
     - Speech-to-text and text-to-speech
     - AI conversation and long-term memory
     - Camera processing and high-level behavior planning
   - The high-level computer sends safe, high-level commands (e.g. STATE=COMFORT, FACE=SAFE). The microcontroller maps these to predefined, safe physical reactions.

## Development Stages

## V0.1 — First Life Sign (Minimal physical reaction)

Goal: Produce a stable, repeatable physical reaction.

Inputs:
- TTP223 capacitive touch sensor (or a push button)

Controller:
- ESP8266 (from a starter kit for first prototype)
- The ESP8266 will read the touch sensor, control a WS2812B LED ring, drive a passive buzzer, and send a control signal to one servo.

Outputs:
- WS2812B LED ring (12 LEDs)
- KY-006 passive buzzer
- One MG90S/SG90 servo

States: IDLE, TOUCHED (possible later: SHY, HAPPY, SAFE, SLEEPY, COMFORT)

Definition of Done:
- Reliable touch detection
- Non-blocking LED heartbeat
- Controlled buzzer sound
- Safe servo movement
- Full reaction repeats and returns to IDLE
- Wiring and program documented in the repository

## V0.2 — Emotional State Machine

Goal: Implement multiple consistent physical states without AI.

Possible states: IDLE, TOUCHED, SHY, HAPPY, SAFE, SLEEPY, COMFORT

Improvements to implement:
- Non-blocking timing and cleaner functions
- Multiple touch zones and smoother servo movement
- More expressive LED patterns and stable wiring
- Calibrated reaction durations

Possible touch zones: head, chest, left arm, right arm, back

### V0.3 — Display Face Prototype

Goal: Add a digital face with animated eyes and expressions.

Hardware candidates:
- ESP32-S3
- 2–3.5" IPS/TFT display
- Black transparent or glossy face panel
- Custom 3D-printed head enclosure

Animations to prototype: open/blink/closed eyes, happy/shy/look left/right, listening/thinking/sleepy states.
Prototype animations on a computer before committing to a display.

### V0.4 — Laptop-to-Robot Bridge

Goal: Connect the prototype to the AI running on a laptop.

Possible communications: USB serial, Wi‑Fi, local network messages.

Example command (JSON):

{
  "state": "comfort",
  "face": "eyes_closed_safe",
  "heartbeat": "slow_warm",
  "motion": "small_hug"
}

The microcontroller executes a safe predefined reaction when receiving such commands.

### V1 — Standalone Desktop Companion

Goal: Build the first self-contained companion version.

Possible hardware:
- ESP32-S3 (physical controller)
- Raspberry Pi (high-level computer)
- Digital face display, microphone, speaker, amplifier
- Multiple touch zones, LED heartbeat, small arms, stable enclosure

Behaviors:
- Natural blinking, touch response, listen and answer, remember information, coordinated light/face/sound/motion reactions

Walking is not required for this version.

### V2 — Rolling Companion Base

Goal: Allow safe movement with wheels rather than bipedal walking.

Possible parts: DC motors, motor driver, wheels, chassis, ultrasonic or ToF sensors, wheel encoders, bumpers, camera.

Behaviors:
- Detect user → approach slowly → stop at safe distance → look toward user → open arms

Develop the rolling base before attempting humanoid walking.

### V3 — Humanoid Upper Body

Goal: Create a more expressive humanoid upper body (moving head, shoulders, elbows, small hands, torso control, hugging motion).

Before choosing servos:
- Create a CAD model, determine arm lengths and mass, calculate required torque, define mechanical limits, and design safe movement sequences.

### V4 — Advanced Humanoid Movement

Goal: Research standing, balance and walking (hip/knee/ankle joints, IMU, COM estimation, motion planning, ROS2, camera-based perception).
This is a long-term research stage; Huggy can still be useful and expressive long before walking is completed.

## Inputs (examples)

- Capacitive touch, buttons, ultrasonic/ToF distance, microphone, camera, IMU, temperature, pressure/contact sensors, wheel encoders

## Outputs (examples)

- LED heartbeat, passive buzzer, digital face, speaker/voice, head/arm movement, wheel motors, body posture and humanoid movement

## Power Architecture

Phase A — Logic tests:
- USB → ESP8266 (low-brightness LED ring)
- Never power motors/servos from ESP GPIO or 3.3V pins

Phase B — One servo test:
- USB → ESP8266
- Separate 4×AA supply → servo
- Common ground between ESP and servo supply

Phase C — Battery prototype:
- Battery pack branching into regulated lines for controller/sensors/display, servos, and motors
- Use verified battery packs, correct chargers, protection/BMS, fuses, main switch, and measure converters before connecting
- Keep logic power isolated from servo/motor noise
- Do not test unknown batteries without supervision

Note: Existing 18650 cells must be verified before use (condition, configuration, protection).

## Mechanical & Environmental Considerations

- Define enclosure mounting points, connector accessibility, and cable routing
- Specify operating temperature and humidity ranges and select rated components
- Consider EMI/EMC shielding and grounding strategies

## PCB & Layout Guidelines

- Separate analog and digital grounds and join at a single point if needed
- Place decoupling capacitors close to power pins
- Route high-speed signals with controlled impedance and avoid long parallel traces for sensitive signals
- Place connectors and test points for manufacturing and debugging

## Connectors & Pinouts

Provide a final pinout table in an appendix: connector type, pin number, signal, voltage level, and direction.

## Testing & Validation

- Unit tests for subsystems (sensors, actuators, comms)
- Integration tests and acceptance criteria (battery run time, response latency)
- Calibration procedures for manufacturing and field service

## Engineering Principle

Build in validated stages with clear goals, acceptance tests, documented wiring and code, safety limits, and a short development log.

## Revision History

- 1.0 — Initial formatted hardware architecture document
