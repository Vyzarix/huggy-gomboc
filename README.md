# Huggy Gomboc

Huggy Gomboc is a small emotional companion robot prototype.

The goal is to build a little robot companion that can react to touch, presence and later voice with light, sound, movement and simple personality states.

## Magyar leírás

A Huggy Gombóc / Ölelő Gombóc célja egy kicsi companion robot építése, amely érintésre, közelségre és később hangra reagál fénnyel, mozgással, hanggal és egyszerű személyiségállapotokkal.

A projekt hosszú távon nem csak egy egyszerű robotautó vagy Arduino-kísérlet, hanem egy többéves mérnöki tanulási projekt:

* robotika
* mikrokontrolleres vezérlés
* szenzorok
* LED-effektek
* szervómozgás
* energiaellátás
* később AI, hang, memória és személyiség
* még később humanoid test és ember-robot interakció

## Core Principle

The project is based on a simple robotics idea:

```text
INPUT → DECISION → OUTPUT
```

The robot senses something, makes a simple decision, then reacts.

Examples:

```text
touch → shy state → heartbeat LED + small servo movement
distance → attention state → turns toward the user
voice → AI response → speech + emotional light
```

## V0.1 Goal

The first version will be a simple reactive system.

The goal of V0.1 is not to build the final humanoid robot yet.
The goal is to create the first “life sign” of Huggy.

### Planned V0.1 reactions

* touch input
* LED heartbeat effect
* passive buzzer sound
* small servo movement

### V0.1 target behavior

```text
touch → LED heartbeat → buzzer sound → small servo movement
```

This will be the first moment where Huggy physically reacts to the user.

## Planned Development Roadmap

### Huggy V0.1 — First Life Sign

Goal:

```text
touch → LED heartbeat → buzzer → small servo movement
```

Main parts:

* ESP8266 from the existing AliExpress robot kit
* TTP223 capacitive touch sensor
* WS2812B 12 LED ring
* KY-006 passive buzzer
* MG90S 180° servo
* USB power for first tests

Focus:

* digital input
* digital output
* PWM
* LED effect
* buzzer sound
* one servo movement
* basic state logic

---

### Huggy V1 — Emotional Reaction Prototype

Goal:

Huggy should have multiple simple emotional states.

Possible states:

* IDLE
* TOUCHED
* SHY
* HAPPY
* SLEEPY
* COMFORT

Example:

```text
head touch → SHY → red/pink heartbeat + small head turn
chest touch → COMFORT → slow heartbeat + soft sound
```

Focus:

* better state machine
* more touch zones
* cleaner wiring
* basic reaction design
* documentation

---

### Huggy V2 — Rolling Base

Goal:

Huggy should be able to move on a simple wheeled base.

Possible parts:

* DC motors from the existing robot kit
* motor driver from the existing robot kit
* ultrasonic distance sensor
* existing wheels and chassis parts

Possible behaviors:

* move forward
* stop before obstacles
* turn
* follow simple distance logic
* later move toward the user

Focus:

* motor control
* obstacle detection
* distance sensing
* safe movement

---

### Huggy V3 — Voice Hardware

Goal:

Huggy should start getting a voice system.

Possible future parts:

* microphone
* speaker
* audio amplifier
* Raspberry Pi or laptop backend

Concept:

```text
microphone → speech-to-text → AI response → text-to-speech → speaker
```

Focus:

* sound input
* sound output
* TTS
* STT
* basic voice interaction

---

### Huggy V4 — Solana / AI Personality

Goal:

Huggy should have an AI conversation layer.

The AI personality may be based on the earlier Solana prototype.

Possible features:

* personality prompt
* memory file
* conversation history
* project assistant behavior
* emotional support behavior
* simple command output for the robot body

Concept:

```text
User message → Solana/Huggy AI → response + emotion command
```

Example command:

```json
{
  "emotion": "comfort",
  "led": "slow_heartbeat",
  "servo": "arms_open",
  "voice": "soft"
}
```

Focus:

* LLM integration
* memory
* personality
* safe emotional companion behavior
* AI-to-robot commands

---

### Huggy V5 — Arms, Head and Hugging Motion

Goal:

Huggy should have more expressive physical movement.

Possible features:

* head movement
* arm movement
* shy reaction
* small hug-like motion
* body posture
* more servos

Focus:

* servo mechanics
* stronger power system
* motion sequences
* safe movement
* expressive body language

---

### Huggy V6 — Humanoid Body Experiments

Goal:

Move toward a more humanoid companion body.

This may include experiments with:

* the school robotics lab humanoid frame
* multiple servos
* servo controller
* stronger power system
* torso, arms, head and maybe legs

Focus:

* humanoid structure
* servo coordination
* mechanical stability
* power distribution
* learning from robotics mentors and teammates

---

### Huggy V7 — Walking, Balance and Advanced Robotics

Goal:

Long-term humanoid movement.

This is a future, advanced stage.

Possible topics:

* center of mass
* foot design
* hip/knee/ankle movement
* IMU sensor
* balance
* motion planning
* ROS / ROS2
* camera-based perception
* AI-assisted behavior

This stage is not the current goal.
It is a long-term direction for learning and development.

## Long-Term Vision

Huggy Gomboc is planned as a long-term engineering project.

The final vision is a small emotional companion robot that can:

* sense touch
* react with heartbeat-like light
* make small emotional sounds
* move its head and arms
* recognize presence
* communicate with voice
* remember important things
* have a gentle AI personality
* become a learning platform for robotics, AI and human-centered technology

The project should grow step by step.

First reaction.
Then movement.
Then voice.
Then memory.
Then personality.
Then a better body.
Then advanced robotics.

## Current Status

Current focus:

* ordering V0.1 parts
* studying the existing ESP8266 robot kit
* understanding factory example codes
* documenting the project on GitHub
* preparing the first touch → LED → buzzer → servo test
