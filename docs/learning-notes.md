  Huggy Gombóc Learning Notes

  This file contains what I learn while building Huggy Gombóc.

  The goals that Huggy should react:

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
Microcontroller

The ESP8266 will be the first main controller for Huggy’s physical reactions.

  What I need to learn:

digital input
digital output
PWM
reading sensor values
controlling LEDs
controlling a passive buzzer
controlling one servo
using Wi-Fi later
writing cleaner functions
building a simple state machine
Touch Sensor

The TTP223 touch sensor works as a simple capacitive touch input.

  Basic idea:

VCC → power
GND → ground
OUT → signal to ESP8266

If touched, OUT changes state.

This can become Huggy’s first “feeling” input.

  Possible future use:

chest touch → heartbeat reaction
head touch → shy reaction
arm touch → comfort reaction
LED Heartbeat

The LED heartbeat is not just decoration.
It gives Huggy emotional presence.

  First version:

slow pulsing light when idle
faster pulse when touched
different colors for different states

  Possible later states:

IDLE → soft slow pulse
TOUCHED → faster pulse
SHY → red/pink pulse
SLEEPY → dim blue/white
COMFORT → slow warm heartbeat
Passive Buzzer

The KY-006 passive buzzer can make simple tones.

It is not real speech.
It is only an early sound reaction.

  What I need to learn:

how to generate a tone
how frequency changes pitch
how to make short beeps
how to create a simple heartbeat-like rhythm

  Later, Huggy will need:

speaker
TTS
microphone
STT
AI conversation layer
Servo

A servo creates physical movement.

  First servo learning goals:

move to 0°
move to 90°
move to 180°
move slowly
react to touch
create a shy movement
Power Safety

First tests should run from USB.

Battery tests should only come later.

  Important rules:

do not short 18650 batteries
do not power servos directly from ESP8266 pins
use buck converter for stable voltage
use common GND
separate logic power and servo/motor power when needed
ask for help from others before battery + servo tests
Existing Robot Kit Learning

The existing AliExpress ESP8266 robot kit is a learning platform.

  Things to study:

motor control code
obstacle avoidance code
ultrasonic sensor code
Wi-Fi control code
SG90 servo code
motor driver wiring
power wiring

This kit can later become a donor platform for Huggy V2 rolling base.

  First Learning Goal

Before building the full robot, I need to understand:

how to blink an LED
how to read a touch sensor
how to make a buzzer sound
how to move one servo
how to combine these into one simple reaction
