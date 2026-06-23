# Huggy Gomboc Architecture

This document describes the planned technical structure of Huggy Gomboc.

## V0.1 Architecture

The first version is a minimal physical reaction system.

### V0.1 Goal

```text
touch → LED heartbeat → buzzer sound → small servo movement
```

The purpose of V0.1 is to create the first “life sign” of Huggy.

## Input Layer

Inputs are the things Huggy can sense.

### V0.1 inputs

* TTP223 capacitive touch sensor
* optional button input from starter kit

### Existing possible inputs from the robot kit I've already had

* HC-SR04 ultrasonic distance sensor
* existing robot kit sensors

### Future inputs

* multiple touch zones
* distance sensor
* microphone
* camera
* IMU
* temperature sensor
* pressure/contact sensors

## Decision Layer

The decision layer decides what Huggy should do.

### V0.1 controller

For the first version, the existing ESP8266 robot kit can be used.

The ESP8266 will:

* read the touch sensor
* control the LED ring
* control the passive buzzer
* move one servo
* run the first simple state logic

### Early state examples

Possible first states:

```text
IDLE
TOUCHED
SHY
HAPPY
SLEEPY
COMFORT
```

Example logic:

```text
if touch sensor is active:
    state = TOUCHED
    LED heartbeat becomes faster
    buzzer makes a short sound
    servo moves slightly
else:
    state = IDLE
    LED heartbeat stays slow
```

## Output Layer

Outputs are the ways Huggy reacts.

### V0.1 outputs

* WS2812B 12 LED ring
* KY-006 passive buzzer
* MG90S 180° servo
* optional existing SG90 servo from the robot kit

### Planned output behaviors

LED:

* slow heartbeat
* fast heartbeat
* shy red/pink color
* calm blue/white color
* sleep-like dim light

Buzzer:

* short beep
* soft reaction sound
* heartbeat-like rhythm
* simple tone pattern

Servo:

* small head turn
* small arm movement
* shy movement
* tiny “alive” motion

## Power Architecture

### First tests

The first tests should run from USB power.

```text
USB → ESP8266 → touch sensor / LED test / buzzer test
```

The first tests should not use batteries yet.

### Later battery system

Later Huggy can use 18650 batteries with buck converters.

Possible future power structure:

```text
Battery pack
 ├── buck converter → logic / ESP / sensors / LED
 ├── buck converter → servos
 └── buck converter → motors or other modules
```

Important:

* use common GND
* do not power servos directly from ESP pins
* do not short 18650 batteries
* ask teammates for help
* keep motor and servo power separated from sensitive logic when needed

## V1 Architecture

Huggy V1 should improve the V0.1 system.

Planned improvements:

* multiple touch zones
* better state machine
* more stable wiring
* cleaner physical layout
* more expressive LED patterns
* more controlled servo motion

Possible touch zones:

```text
head
chest
left arm
right arm
back
```

## V2 Architecture — Rolling Base

Huggy V2 may use parts from the existing AliExpress ESP8266 robot kit.

Possible parts:

* DC motors
* motor driver
* wheels
* robot chassis
* ultrasonic distance sensor

Possible behaviors:

* move forward
* stop before obstacles
* turn
* follow simple distance logic
* move toward the user later

Architecture:

```text
ESP8266 → motor driver → DC motors
ESP8266 → ultrasonic sensor → distance decision
```

## V3 Architecture — Voice Hardware

Later Huggy will need voice input and output.

Possible architecture:

```text
microphone → speech-to-text → AI system → text-to-speech → speaker
```

This will likely require a bigger controller, such as:

* laptop backend
* Raspberry Pi
* later Jetson for AI/vision tasks

## V4 Architecture — AI Personality

The AI layer may be based on my earlier Solana prototype.

Possible AI pipeline:

```text
user text / voice
       ↓
conversation memory
       ↓
Solana / Huggy personality
       ↓
AI response
       ↓
voice output + robot emotion command
```

Example robot command:

```json
{
  "emotion": "comfort",
  "led": "slow_heartbeat",
  "servo": "arms_open"
}
```

The AI layer should not directly replace human relationships.
It should support learning, reflection, focus and emotional expression.

## Future Full System

A future advanced Huggy system may look like this:

```text
Touch / distance / voice / camera
        ↓
Microcontroller reads sensors
        ↓
Raspberry Pi / Jetson handles AI, voice, memory and perception
        ↓
Decision system chooses Huggy state
        ↓
Microcontroller controls LEDs, servos and motors
        ↓
Huggy reacts physically
```

Human analogy:

```text
sensors = senses
ESP8266 = reflex system
Raspberry Pi / Jetson = higher brain
servos / motors = muscles
LED / buzzer / speaker = expression
Solana / Huggy AI = personality
```

## Engineering Principle

Do not build the final humanoid immediately.

Build step by step:

```text
reaction → movement → voice → memory → personality → body → advanced robotics
```
