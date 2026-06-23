    Huggy Gombóc Architecture

The robot receives information from sensors, makes a simple decision, then reacts with light, sound or movement.

  V0.1 system

The first version is not a full humanoid robot yet.
The goal is to create the first emotional reaction system.

  Inputs:

  Planned input sources:

TTP223 capacitive touch sensor
button input
later: distance sensor
later: microphone
later: camera
Decision layer

At first, the decision layer will run on an ESP8266.

The ESP8266 will read sensor values and choose a simple state.

  Planned early states:

IDLE
TOUCHED
SHY
HAPPY
SLEEPY

Example:

if touch sensor is activated:
state = TOUCHED
LED heartbeat becomes faster
buzzer makes a small sound
servo moves slightly

  Outputs

  Planned output devices:

WS2812B LED ring for heartbeat and emotional light
passive buzzer for simple sound reaction
SG90 / MG90S servo for small movements
later: speaker for voice
later: DC motors for rolling movement
later: humanoid servo movements

  V0.1 goal

The first real goal:

touch → LED heartbeat → buzzer sound → small servo movement

This will be the first “life sign” of Huggy.

#Future AI architecture

Later, Huggy will have an AI conversation layer.

#Possible future pipeline:

User voice → Speech-to-Text → LLM / Solana personality → Text-to-Speech → speaker

The physical robot can also receive commands from the AI layer:

AI response → emotion command → ESP8266 → LED / servo / motor reaction

  Example future command:

{
"emotion": "comfort",
"led": "slow_heartbeat",
"servo": "arms_open",
"voice": "soft"
}

  Long-term system vision

Huggy Gombóc may later become a small emotional companion robot with:

touch zones
LED heartbeat
simple emotional states
voice interaction
memory
personality
rolling base
arms
humanoid body experiments
safe and private AI companion behavior

The project should grow step by step.
First: reaction.
Later: movement.
Later: voice.
Later: memory.
Later: humanoid body.
