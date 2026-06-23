  Huggy Gombóc Parts List

  This file contains the planned and existing parts for Huggy Gombóc.

  V0.1 Parts List

The first working behavior should be:

touch → LED heartbeat → buzzer sound → small servo movement

  LM2596 buck converter

Quantity: 3 pieces

  Purpose:

step down battery voltage to stable 5V or 6V
later power servos, LEDs or electronics from batteries
create separate power branches later

  Possible future use:

battery → buck converter → logic / sensors / LED
battery → buck converter → servos
battery → buck converter → motors

  Important:

First tests will run from USB.
Battery tests will come later with help from others.

  WS2812B 12 LED ring

Quantity: 1 piece

  Purpose:

heartbeat effect
emotional light feedback
visual robot state

  Possible states:

slow red pulse → calm heartbeat
faster red pulse → touched / excited
blue or white dim light → idle / sleepy
pink/red → shy reaction

  KY-006 passive buzzer

Quantity: 1 piece

  Purpose:

simple sound feedback
short beep
simple tones
heartbeat-like rhythm
early emotional sound reaction

  Note:

This is not for real speech.
Real voice will require a speaker, TTS and a bigger controller later.

  TTP223 capacitive touch sensor

Quantity: 10 pieces

  Purpose:

touch input
first “feeling” input for Huggy
possible future touch zones

  Possible zones:

chest
head
left arm
right arm
back

  MG90S 180° servo

Quantity: 3 pieces

  Purpose:

small movement
head movement
tiny arm movement
shy reaction
learning servo control

  Already available from my AliExpress ESP8266 robot kit:

ESP8266 controller
DC motors
wheels
motor driver
ultrasonic distance sensor
SG90 servo
small breadboard
jumper wires
robot chassis
existing example programs:
motor control
obstacle avoidance
distance-based behavior
Wi-Fi control

  Available power-related parts:

2× 18650 batteries
18650 battery holder
Optional / Later Parts

  PCA9685 servo controller

For V0.1, it is not required.

  Purpose later:

microcontroller → PCA9685 → multiple servos

Useful when Huggy has more moving parts.

  ESP8266

The ESP8266 will be the first controller for Huggy’s physical reaction system.

  It can be used for:

reading the TTP223 touch sensor
controlling the WS2812B LED ring
controlling the KY-006 passive buzzer
moving one simple servo
learning basic Wi-Fi control later
testing the first INPUT → DECISION → OUTPUT logic

The existing ESP8266 is enough for the first V0.1 tests, so a new controller is not needed yet.

  Limitations:

The ESP8266 is good for the first prototype, but later Huggy may outgrow it because it has fewer GPIO pins and less flexibility than an ESP32.

An ESP32 may be useful later because it has:

more GPIO pins
more future flexibility
Wi-Fi
Bluetooth / BLE
better support for multiple sensors and outputs

  Raspberry Pi

Status:

Future part.

  Purpose later:

AI / Solana backend
memory
microphone
speaker
TTS
STT
camera
higher-level behavior

Important:

A Raspberry Pi does not fully replace the microcontroller.
The likely future system is:

Raspberry Pi = AI / voice / memory
ESP8266 or ESP32 = sensors / LEDs / servos / motors
V0.1 Minimum Build

  Minimum working system:

ESP8266
TTP223 touch sensor
WS2812B LED ring
KY-006 passive buzzer
MG90S or SG90 servo
USB power
