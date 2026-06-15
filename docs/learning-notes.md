Huggy Gombóc Learning Notes

This file contains what I learn while building Huggy Gombóc.

Core robotics principle

The whole project is based on:

INPUT → DECISION → OUTPUT

Input means the robot senses something.

Examples:

touch
button press
distance
sound
camera image

Decision means the robot chooses what to do.

Examples:

idle
touched
shy
happy
comfort mode

Output means the robot reacts.

Examples:

LED heartbeat
buzzer sound
servo movement
motor movement
voice
ESP32

The ESP32 will be the first main controller for Huggy’s physical reactions.

What I need to learn:

digital input
digital output
PWM
reading sensor values
controlling LEDs
controlling buzzer
controlling servo
using Wi-Fi later
Touch sensor

The TTP223 touch sensor works as a simple capacitive touch input.

Basic idea:

VCC → power
GND → ground
OUT → signal to ESP32

If touched, OUT changes state.

This can become Huggy’s first “feeling” input.

LED heartbeat

The LED heartbeat is not just decoration.
It gives Huggy emotional presence.

First version:

slow pulsing light when idle
faster pulse when touched
different colors for different states
Buzzer

The passive buzzer can make simple tones.

It is not real speech.
It is only an early sound reaction.

Later, Huggy will need:

speaker
TTS
microphone
STT
AI conversation layer
Servo

A servo creates physical movement.

Important:

180° servo = position control
360° servo = continuous rotation, more like a motor

For Huggy’s head or arms, 180° servos are needed.

Power safety

First tests should run from USB.

Battery tests should only come later.

Important rules:

do not short 18650 batteries
do not power servos directly from ESP32 pins
use buck converter for stable voltage
use common GND
ask for help in the robotics lab before battery + servo tests
First learning goal

Before building the full robot, I need to understand:

how to blink an LED
how to read a touch sensor
how to make a buzzer sound
how to move one servo
how to combine these into one simple reaction
