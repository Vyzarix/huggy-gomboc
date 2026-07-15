# Huggy Gombóc Hardware Learning Notes

This file contains the hardware and embedded-system concepts I learn while building Huggy Gombóc.

The AI and conversation software are documented separately.

---

# Core Robotics Principle

Huggy's physical system follows:

```text
INPUT → STATE / DECISION → OUTPUT

Input means the robot detects something.

Examples:

touch
button press
distance
sound
camera image
movement
orientation

State or decision means the robot chooses a controlled behavior.

Examples:

IDLE
TOUCHED
SHY
HAPPY
SAFE
SLEEPY
COMFORT
LISTENING
THINKING

Output means the robot reacts.

Examples:

LED heartbeat
digital eyes
buzzer sound
voice
servo movement
motor movement
Controller Types
Microcontroller

Examples:

ESP8266
ESP32
Arduino boards

Purpose:

read sensors
control outputs
generate precise physical reactions
run safety limits
react quickly

For Huggy V0.1, the ESP8266 is the first physical controller.

High-Level Computer

Examples:

laptop
Raspberry Pi
Jetson

Purpose:

run Linux
process voice
handle AI communication
manage memory
process camera data
send high-level commands to the physical controller

A Raspberry Pi does not completely replace the microcontroller.

Likely architecture:

high-level computer
→ behavior command
→ microcontroller
→ safe physical reaction
ESP8266 Learning Goals

I need to learn:

digital input
digital output
PWM
non-blocking timing
reading sensor values
controlling LEDs
controlling a passive buzzer
controlling one servo
using functions
using enums or named states
building a simple state machine
basic serial communication
basic Wi-Fi communication later
Touch Sensor

The TTP223 is a capacitive touch sensor.

Basic connections:

VCC → power
GND → ground
OUT → ESP8266 input

When touch is detected, the OUT signal changes state.

Possible reactions:

chest touch → heartbeat reaction
head touch → SAFE or SHY reaction
arm touch → COMFORT reaction

One sensor should be tested before connecting multiple touch zones.

LED Heartbeat

The LED heartbeat is not only decoration.

It creates emotional presence and shows Huggy's current state.

Possible states:

IDLE → slow pulse
TOUCHED → faster pulse
SHY → pink or red pulse
SLEEPY → dim blue or white
COMFORT → slow warm heartbeat
SAFE → very calm pulse

Learning goals:

control WS2812B pixels
set brightness safely
create smooth fading
create non-blocking heartbeat timing
change color based on state
Passive Buzzer

The KY-006 passive buzzer can create tones.

It is not a speaker and cannot produce normal speech.

Learning goals:

generate a tone
change pitch with frequency
create short beeps
create a heartbeat-like pattern
create different state sounds
stop sounds without blocking other reactions

Future voice requires:

microphone
speech-to-text
text-to-speech
speaker
amplifier
high-level computer
Servo

A servo creates position-controlled movement.

Servo wires normally represent:

VCC
GND
signal

The control signal comes from the microcontroller.

The servo power should come from a suitable separate supply.

The grounds must share a common reference.

First servo goals:

move to a safe center position
define minimum and maximum safe angles
move slowly
react to touch
return to a neutral position
create a shy or safe movement
avoid mechanical collisions

Never assume that every servo can safely move from 0° to 180° inside a mechanism.

Mechanical limits must be tested carefully.

Common Ground

When the ESP8266 and servo use different power sources:

ESP8266 GND
servo power GND
servo GND

must be electrically connected.

The breadboard ground rail may be used as a temporary common connection point.

The servo VCC must not be connected to the ESP8266 3.3 V pin.

Power Domains

A robot may contain separate power branches.

Examples:

logic power
servo power
motor power
audio power

They may use different voltage regulators but still require a correctly designed common reference.

Learning goals:

measure voltage with a multimeter
identify positive and negative terminals
adjust a buck converter
understand current requirements
avoid reverse polarity
understand battery series and parallel connections
understand why motors and servos create electrical noise
use a fuse and power switch later
Battery Safety

Important rules:

do not short battery terminals
do not use damaged cells
do not mix cells of unknown condition
do not charge lithium cells with an incorrect charger
verify whether cells are connected in series or parallel
use battery protection when required
measure voltage before connecting electronics
begin battery tests with supervision

The existing 18650 cells should not be used until they are inspected and verified.

Existing Robot Kit Learning

The existing ESP8266 robot kit is a separate learning platform.

Topics to study:

motor control code
motor driver wiring
ultrasonic sensor code
obstacle avoidance
Wi-Fi control
SG90 servo control
power wiring
program structure

Possible future use:

existing robot kit
→ rolling-base experiments
→ later Huggy V2 donor platform

The kit should not be dismantled until its existing programs and wiring are documented.

Digital Face Learning

The digital face will be developed after the first physical reaction system.

Topics to learn:

display resolution
SPI or parallel display communication
drawing basic shapes
frame rate
blinking animation
state-based expressions
black face background
synchronization with movement and heartbeat

Possible state mapping:

IDLE → natural blinking
SAFE → eyes closed
SHY → look down or sideways
HAPPY → curved eyes
LISTENING → focused eyes
THINKING → small animated movement
Testing Method

Every part should be tested separately.

Recommended order:

1. ESP8266 basic program
2. normal LED or serial output
3. TTP223 touch sensor
4. WS2812B LED ring
5. KY-006 passive buzzer
6. one servo with separate power
7. simple state machine
8. combined V0.1 reaction
9. repeated stability test
10. documentation

Do not connect every component at once before the individual tests work.

V0.1 Learning Goal

Before building the full robot, I need to understand:

how to read a touch sensor
how to create a smooth heartbeat
how to create a controlled sound
how to move one servo safely
how to use a shared ground
how to structure the program
how to combine components without blocking
how to document the wiring and code

First complete behavior:

touch
→ state changes to TOUCHED
→ heartbeat becomes faster
→ buzzer plays a short sound
→ servo moves slowly
→ state returns to IDLE
