# Huggy Gomboc Hardware Architecture

This document describes the planned hardware architecture of Huggy Gomboc.

The AI, memory and conversation software are documented separately.
This file focuses on sensors, controllers, power, displays, sound and physical movement.

## Core Hardware Principle

Huggy's physical system follows a simple robotics structure:

```text
INPUT → STATE / COMMAND → OUTPUT

Examples:

touch → SAFE state → eyes close + slow heartbeat
touch → SHY state → pink heartbeat + small head turn
distance detected → ATTENTION state → face looks toward the user
AI command → COMFORT state → arms open + soft voice
Controller Layers

The long-term system will use two different controller layers.

Low-Level Physical Controller

Possible controllers:

ESP8266 for the first prototype
ESP32 or ESP32-S3 for later versions

Responsibilities:

read touch sensors
control the LED heartbeat
control the display face
control servos and motors
run safe predefined movement sequences
react quickly even when the AI system is unavailable
High-Level Computer

Possible systems:

laptop during development
Raspberry Pi in a standalone version
Jetson later if advanced local vision is required

Responsibilities:

microphone and speaker
speech-to-text
text-to-speech
AI conversation
long-term memory
camera processing
high-level behavior commands

The high-level computer should not directly create uncontrolled servo movements.

Instead, it should send safe commands such as:

STATE=COMFORT
FACE=SAFE
MOTION=OPEN_ARMS
HEARTBEAT=SLOW

The microcontroller will convert these commands into predefined physical reactions.

V0.1 — First Life Sign
Goal

The first version is a minimal physical reaction system.

touch → LED heartbeat → buzzer sound → small servo movement

The purpose of V0.1 is to create the first stable physical reaction of Huggy.

It is not intended to be a complete robot body.

Inputs
TTP223 capacitive touch sensor
optional push button from the electronics starter kit
Controller
existing ESP8266 from the AliExpress robot kit

The ESP8266 will:

read one touch sensor
control the WS2812B LED ring
control the passive buzzer
send a control signal to one servo
run the first simple state logic
Outputs
WS2812B 12 LED ring
KY-006 passive buzzer
one MG90S or SG90 servo
First States
IDLE
TOUCHED

Possible later V0.1 states:

SHY
HAPPY
SAFE
SLEEPY
COMFORT
Example Logic
if touch is detected:
    change state to TOUCHED
    increase heartbeat speed
    play a short sound
    move the servo slowly
else:
    stay in IDLE
    display a slow heartbeat
V0.1 Definition of Done

V0.1 is complete when:

all components work separately
touch detection is reliable
the LED heartbeat runs without blocking the whole program
the buzzer can create a short controlled sound
one servo moves safely
the full reaction works repeatedly
Huggy returns to IDLE after the reaction
the wiring is documented
the program is stored in the repository
V0.2 — Emotional State Machine
Goal

Create multiple consistent physical states without AI.

Possible states:

IDLE
TOUCHED
SHY
HAPPY
SAFE
SLEEPY
COMFORT

Possible reactions:

head touch
→ SAFE
→ slow warm heartbeat
→ eyes closed later
→ small movement toward the hand
unexpected touch
→ SHY
→ faster pink heartbeat
→ small turn away
→ return to IDLE

Planned improvements:

cleaner functions
non-blocking timing
multiple touch zones
smoother servo movement
more expressive LED patterns
more stable wiring
calibrated reaction durations

Possible touch zones:

head
chest
left arm
right arm
back
V0.3 — Display Face Prototype
Goal

Add a digital face with animated eyes.

The face should be able to display:

open eyes
blinking
closed safe eyes
happy eyes
shy eyes
looking left and right
listening state
thinking state
sleepy state

Possible future hardware:

ESP32-S3
approximately 2–3.5 inch IPS or TFT display
black transparent or glossy face panel
custom 3D-printed head enclosure

Possible reaction:

head touch
→ SAFE state
→ eyes slowly close
→ heartbeat slows down
→ head moves slightly toward the hand

The face animations should first be prototyped on a computer before buying the final display.

V0.4 — Laptop-to-Robot Bridge
Goal

Connect the physical prototype to the developing Huggy AI running on a laptop.

Possible communication methods:

USB serial
Wi-Fi
local network messages

Example command:

{
  "state": "comfort",
  "face": "eyes_closed_safe",
  "heartbeat": "slow_warm",
  "motion": "small_hug"
}

The ESP8266 or ESP32 will receive the command and execute a safe predefined reaction.

This stage proves that the AI and the physical robot can work together before purchasing a Raspberry Pi.

V1 — Standalone Desktop Companion
Goal

Create the first self-contained companion version of Huggy.

Possible hardware:

ESP32-S3 physical controller
Raspberry Pi high-level computer
digital face display
microphone
speaker
audio amplifier
head movement
multiple touch zones
LED heartbeat
small arms
stable enclosure

Possible behaviors:

blink naturally
close the eyes when the head is touched
listen and answer
remember selected information
move the head
open the arms
react with light, face, sound and motion together

Walking is not required for this version.

V2 — Rolling Companion Base
Goal

Allow Huggy to move safely without requiring bipedal walking.

Possible reusable parts from the existing robot kit:

DC motors
motor driver
wheels
chassis components
ultrasonic distance sensor

Possible later sensors:

ToF distance sensors
wheel encoders
camera
bumper sensors

Possible behaviors:

detect user
→ approach slowly
→ stop at a safe distance
→ look toward the user
→ open arms

The rolling base should be developed before attempting humanoid walking.

V3 — Humanoid Upper Body
Goal

Create a more expressive humanoid body.

Possible features:

moving head
two shoulders
two elbows
small hands
torso
hugging motion
body posture
stronger or smarter servos
rigid internal frame
3D-printed outer shell

Before choosing final servos:

create a CAD model
determine arm lengths
estimate component mass
calculate required torque
define mechanical limits
design safe movement sequences
V4 — Advanced Humanoid Movement
Goal

Research standing, balance and eventually walking.

Possible requirements:

hip, knee and ankle joints
IMU
center-of-mass estimation
stable feet
fall detection
motion planning
coordinated servo control
ROS 2
camera-based perception
extensive testing

This is a long-term research stage.

Huggy can become a useful and emotionally expressive companion long before walking is completed.

Input Layer

Current and future inputs may include:

capacitive touch
buttons
ultrasonic distance
ToF distance
microphone
camera
IMU
temperature sensing
pressure or contact sensors
wheel encoders
Output Layer

Current and future outputs may include:

LED heartbeat
passive buzzer
digital face display
speaker and voice
head movement
arm movement
wheel motors
body posture
humanoid movement
Power Architecture
Phase A — Logic Tests

For touch, button and basic buzzer tests:

USB → ESP8266

The LED ring should initially run at low brightness.

Do not power motors or servos from an ESP8266 GPIO or 3.3 V pin.

Phase B — One Servo Test

Possible first setup:

USB → ESP8266

separate 4×AA supply → one servo

ESP8266 GND
servo supply GND
servo GND
→ common ground

The ESP8266 only provides the servo control signal.

Phase C — Battery Prototype

A later battery architecture may use a verified battery pack:

battery pack
 ├── regulated branch → controller / sensors / display
 ├── high-current regulated branch → servos
 └── regulated branch → motors

Important:

verify battery configuration before use
use the correct charger
use battery protection / BMS when required
use fuses and a main power switch later
measure converter output before connecting electronics
keep logic power isolated from servo and motor noise where necessary
connect grounds correctly
do not test unknown batteries without supervision

The existing 18650 cells should not be used until their condition, configuration and protection are verified.

Engineering Principle

Do not attempt to build the final humanoid immediately.

Build in validated stages:

single reaction
→ emotional states
→ digital face
→ AI connection
→ standalone companion
→ rolling movement
→ humanoid upper body
→ advanced walking

Every stage should have:

a clear goal
an acceptance test
documented wiring
documented code
safety limits
a short development log
