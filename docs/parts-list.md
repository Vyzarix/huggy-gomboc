**Huggy Gombóc Parts List**

This file contains the first planned parts for Huggy Gombóc V0.1.

Main controller
ESP32 development board with expansion board

Purpose:

reads sensors
controls LED ring
controls buzzer
sends servo signals
later can communicate over Wi-Fi / Bluetooth

Reason:

ESP32 has more pins and more future potential than ESP8266.

Touch sensing
TTP223 capacitive touch sensor

Purpose:

detects touch
can be used for head, chest, arm or body touch zones

Planned use:

chest touch → heartbeat reaction
head touch → shy reaction
arm touch → small movement reaction
Light
WS2812B RGB LED ring

Purpose:

heartbeat effect
emotional light feedback
color-based state display

Examples:

slow red pulse → calm heartbeat
faster pulse → touched / excited
soft blue/white → sleepy / idle
red/pink → shy reaction
Sound
KY-006 passive buzzer

Purpose:

simple sound feedback
small beeps
simple tones
possible heartbeat-like sound pattern

Note:

This is not for real speech.
Real voice will require a speaker and TTS later.

Movement
SG90 servo

Purpose:

small test movements
head or tiny arm movement
learning servo control

Important:

For Huggy’s head or arms, 180° servo is needed, not 360° continuous rotation.

MG90S servo

Purpose:

stronger movement than SG90
possible arm or head movement
better for later prototypes
Servo controller
PCA9685 16-channel servo driver

Purpose:

controls multiple servos
useful when Huggy gets more moving parts
useful for later humanoid experiments

Architecture:

ESP32 → PCA9685 → servos

Power
LM2596 buck converter

Purpose:

steps down battery voltage to stable 5V or 6V
later used for servos and electronics

Important:

First tests will run from USB.
Battery power will be tested later with help in the robotics lab.

Prototyping
MB102 breadboard

Purpose:

test circuits without soldering
connect ESP32, sensors, LED, buzzer and small components
Electronics starter kit

Purpose:

LEDs
resistors
buttons
capacitors
basic components for learning and testing
Existing parts at home

Already available:

AliExpress ESP8266 robot car kit
DC motors
wheels
motor driver
ultrasonic distance sensor
small breadboard
jumper wires
2× 18650 batteries
18650 battery holder
robot chassis
existing example programs for motor control, obstacle avoidance and Wi-Fi control
V0.1 minimum build

Minimum required working system:

ESP32
TTP223 touch sensor
WS2812B LED ring
KY-006 passive buzzer
breadboard
jumper wires
USB power

Goal:

touch → heartbeat LED → sound reaction
