# Huggy Gombóc Hardware Parts List

This file contains the planned, existing and future hardware parts for Huggy Gombóc.

The Huggy AI software is documented separately.

---

# V0.1 Goal

The first working behavior should be:

```text
touch → LED heartbeat → buzzer sound → small servo movement
Planned V0.1 Order
LM2596 Buck Converter

Quantity:

3 pieces

Purpose:

reduce a higher battery voltage
create regulated power branches later
test basic voltage conversion
power future electronics when correctly configured

Possible future architecture:

battery → converter → controller / sensors / display
battery → suitable converter → servos
battery → suitable converter → motors

Important:

the converter is not required for the first USB logic test
the output must be measured before connecting a device
these small modules are not intended to power the complete school humanoid
real current requirements must be calculated before using them with multiple servos
WS2812B 12 LED Ring

Quantity:

1 piece

Purpose:

heartbeat effect
emotional light feedback
visual robot state

Possible states:

slow red pulse → calm heartbeat
faster pulse → touched or excited
dim blue or white → idle or sleepy
pink or red → shy
warm slow pulse → comfort

Important:

begin with low brightness
do not assume the ESP8266 regulator can power the ring at maximum brightness
use a suitable 5 V supply if required
a logic-level converter may be added later if the data signal is unstable
KY-006 Passive Buzzer

Quantity:

1 piece

Purpose:

simple sound feedback
short beeps
simple tones
heartbeat-like rhythm
early emotional sound reactions

This is not a speech system.

Real voice will later require:

speaker
audio amplifier
text-to-speech
high-level computer
TTP223 Capacitive Touch Sensor

Quantity:

10 pieces

Purpose:

detect touch
create Huggy's first physical input
create multiple touch zones later

Possible zones:

head
chest
left arm
right arm
back

V0.1 will initially use only one sensor.

MG90S 180° Servo

Quantity:

3 pieces

Purpose:

learn servo position control
create small head or arm movements
create a shy movement
create a small “alive” motion

V0.1 will initially use only one servo.

The other servos provide:

backup hardware
later multi-joint experiments
two-arm or head prototypes
Planned Electronics Starter Kit

Possible included parts:

400-point breadboard
basic LEDs
resistors
push buttons
capacitors
jumper wires
small electronic components

Purpose:

practice basic circuits
test digital inputs and outputs
learn breadboard connections
build temporary prototypes without soldering
Existing Parts
Existing ESP8266 Robot Kit

Available parts:

ESP8266 controller
DC motors
wheels
motor driver
ultrasonic distance sensor
SG90 servo
small breadboard
jumper wires
robot chassis

Existing example programs:

motor control
obstacle avoidance
distance-based behavior
Wi-Fi control

The robot kit will initially remain a learning platform.

Its parts may later be reused for the Huggy rolling base.

Existing Power Parts

Available:

2× 18650 cells
2-cell 18650 holder
4×AA battery holder

Current decision:

do not use the existing 18650 cells until they are verified
use USB for the ESP8266 logic tests
use a separate verified supply for servo tests
connect the controller and servo supply grounds correctly
V0.1 Controller
ESP8266

Status:

already available

Purpose:

read the TTP223 touch sensor
control the LED heartbeat
control the passive buzzer
send one servo control signal
run the first physical state machine
learn basic Wi-Fi communication later

Planned chain:

TTP223 → ESP8266 → LED / buzzer / servo command

Why it is used first:

it is already available
it is sufficient for the first simple prototype
it allows the project to start without buying a new controller

Limitations:

fewer GPIO options than modern ESP32 boards
less suitable for a larger display
less flexible for many sensors and outputs
no Bluetooth / BLE
more limited for future expansion
Future Physical Controller
ESP32 or ESP32-S3

Status:

future part

Possible purpose:

digital face display
multiple touch zones
more sensors
multiple communication channels
Wi-Fi and Bluetooth / BLE
communication with Raspberry Pi
more complex physical state machine

An ESP32-S3 may become the main physical controller when the digital face is added.

Future Digital Face Hardware

Possible parts:

approximately 2–3.5 inch IPS or TFT display
ESP32-S3
black face panel
3D-printed head enclosure
optional ambient light sensor

Possible expressions:

open eyes
blink
eyes closed
happy eyes
shy eyes
listening
thinking
sleepy

The exact display should not be purchased until the head dimensions and controller are selected.

Future Voice Hardware

Possible parts:

microphone
speaker
small audio amplifier
Raspberry Pi or other high-level computer

Purpose:

speech input
speech output
AI conversation
listening and speaking states

The passive buzzer is not a replacement for the future speaker.

Future High-Level Computer
Raspberry Pi

Status:

future part

Purpose:

AI client or local AI services
memory
microphone
speaker
speech-to-text
text-to-speech
camera
high-level behavior
communication with the physical controller

Architecture:

Raspberry Pi = AI / voice / memory / vision
ESP8266 or ESP32 = sensors / face / LEDs / servos / motors

A laptop should be used to test this architecture before purchasing a Raspberry Pi.

Optional Servo Controller
PCA9685

Status:

not required for V0.1

Possible purpose:

generate control signals for multiple servos
reduce the number of microcontroller pins required
test coordinated multi-servo movement

Possible architecture:

microcontroller → I2C → PCA9685 → servo control signals

Important:

the PCA9685 does not provide the required servo power by itself
the servos require a separate suitable power supply
controller ground, servo driver ground and servo power ground must be connected correctly
V0.1 Minimum Build

Required:

existing ESP8266
one TTP223 touch sensor
WS2812B LED ring
KY-006 passive buzzer
one MG90S or SG90 servo
breadboard
jumper wires
USB power for the ESP8266
separate suitable power for the servo

First target:

touch
→ faster LED heartbeat
→ short buzzer sound
→ small servo movement
→ return to IDLE
Not Required Yet

Do not purchase yet:

full humanoid servo set
final battery pack
Raspberry Pi
Jetson
final display
final speaker system
final humanoid body
walking hardware

These parts should be selected only after the previous prototype stage works.
