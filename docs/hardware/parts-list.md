# Huggy Gombóc Hardware Parts List

This file contains the planned, existing and future hardware parts for Huggy Gombóc.

The Huggy AI software is documented separately.

---

## V0.1 Goal

The first working behavior should be:

```
touch → LED heartbeat → buzzer sound → small servo movement
```

---

## Planned V0.1 Order

## LM2596 Buck Converter

**Quantity:** 2 pieces

**Purpose:**
- Reduce a higher battery voltage
- Create regulated power branches later
- Test basic voltage conversion
- Power future electronics when correctly configured

**Possible future architecture:**
- Battery → converter → controller / sensors / display
- Battery → suitable converter → servos
- Battery → suitable converter → motors

**Important:**
- The converter is not required for the first USB logic test
- The output must be measured before connecting a device
- These small modules are not intended to power the complete school humanoid
- Real current requirements must be calculated before using them with multiple servos

---

## WS2812B 12 LED Ring

**Quantity:** 1 piece

**Purpose:**
- Heartbeat effect
- Emotional light feedback
- Visual robot state

**Possible states:**
- Slow red pulse → calm heartbeat
- Faster pulse → touched or excited
- Dim blue or white → idle or sleepy
- Pink or red → shy
- Warm slow pulse → comfort

**Important:**
- Begin with low brightness
- Do not assume the ESP8266 regulator can power the ring at maximum brightness
- Use a suitable 5 V supply if required
- A logic-level converter may be added later if the data signal is unstable

---

## KY-006 Passive Buzzer

**Quantity:** 1 piece

**Purpose:**
- Simple sound feedback
- Short beeps
- Simple tones
- Heartbeat-like rhythm
- Early emotional sound reactions

**Note:** This is not a speech system.

**Real voice will later require:**
- Speaker
- Audio amplifier
- Text-to-speech
- High-level computer

---

## TTP223 Capacitive Touch Sensor

**Quantity:** 4 pieces

**Purpose:**
- Detect touch
- Create Huggy's first physical input
- Create multiple touch zones later

**Possible zones:**
- Head
- Chest
- Left arm
- Right arm
- Back

**Note:** V0.1 will initially use only one sensor.

---

## MG90S 180° Servo

**Quantity:** 2 pieces

**Purpose:**
- Learn servo position control
- Create small head or arm movements
- Create a shy movement
- Create a small "alive" motion

**Note:** V0.1 will initially use only one servo.

**The other servos provide:**
- Backup hardware
- Later multi-joint experiments
- Two-arm or head prototypes

---

## Already available:

- mini solderless breadboard
- jumper wires
- ESP8266 expansion board

Parts may be borrowed from the school robotics lab when needed:

- larger breadboard
- resistors
- capacitors
- push buttons
- additional jumper wires

---

## Existing Parts

## Existing ESP8266 Robot Kit

**Available parts:**
- ESP8266 controller
- DC motors
- Wheels
- Motor driver
- Ultrasonic distance sensor
- SG90 servo
- Small breadboard
- Jumper wires
- Robot chassis

**Existing example programs:**
- Motor control
- Obstacle avoidance
- Distance-based behavior
- Wi-Fi control

**Note:** The robot kit will initially remain a learning platform. Its parts may later be reused for the Huggy rolling base.

---

## Existing Power Parts

**Available:**
- 2× 18650 cells
- 2-cell 18650 holder
- 4×AA battery holder

**Current decision:**
- Do not use the existing 18650 cells until they are verified
- Use USB for the ESP8266 logic tests
- Use a separate verified supply for servo tests
- Connect the controller and servo supply grounds correctly

---

## V0.1 Controller

## ESP8266

**Status:** Already available

**Purpose:**
- Read the TTP223 touch sensor
- Control the LED heartbeat
- Control the passive buzzer
- Send one servo control signal
- Run the first physical state machine
- Learn basic Wi-Fi communication later

**Planned chain:**
```
TTP223 → ESP8266 → LED / buzzer / servo command
```

**Why it is used first:**
- It is already available
- It is sufficient for the first simple prototype
- It allows the project to start without buying a new controller

**Limitations:**
- Fewer GPIO options than modern ESP32 boards
- Less suitable for a larger display
- Less flexible for many sensors and outputs
- No Bluetooth / BLE
- More limited for future expansion

---

## Future Hardware

### Future Physical Controller

**Status:** Future part

**Possible options:** ESP32 or ESP32-S3

**Possible purpose:**
- Digital face display
- Multiple touch zones
- More sensors
- Multiple communication channels
- Wi-Fi and Bluetooth / BLE
- Communication with Raspberry Pi
- More complex physical state machine

**Note:** An ESP32-S3 may become the main physical controller when the digital face is added.

---

### Future Digital Face Hardware

**Possible parts:**
- Approximately 2–3.5 inch IPS or TFT display
- ESP32-S3
- Black face panel
- 3D-printed head enclosure
- Optional ambient light sensor

**Possible expressions:**
- Open eyes
- Blink
- Eyes closed
- Happy eyes
- Shy eyes
- Listening
- Thinking
- Sleepy

**Important:** The exact display should not be purchased until the head dimensions and controller are selected.

---

### Future Voice Hardware

**Possible parts:**
- Microphone
- Speaker
- Small audio amplifier
- Raspberry Pi or other high-level computer

**Purpose:**
- Speech input
- Speech output
- AI conversation
- Listening and speaking states

**Note:** The passive buzzer is not a replacement for the future speaker.

---

### Future High-Level Computer

**Status:** Future part

**Proposed:** Raspberry Pi

**Purpose:**
- AI client or local AI services
- Memory
- Microphone
- Speaker
- Speech-to-text
- Text-to-speech
- Camera
- High-level behavior
- Communication with the physical controller

**Proposed architecture:**
```
Raspberry Pi = AI / voice / memory / vision
ESP8266 or ESP32 = sensors / face / LEDs / servos / motors
```

**Note:** A laptop should be used to test this architecture before purchasing a Raspberry Pi.

---

### Optional Servo Controller

**Part:** PCA9685

**Status:** Not required for V0.1

**Possible purpose:**
- Generate control signals for multiple servos
- Reduce the number of microcontroller pins required
- Test coordinated multi-servo movement

**Possible architecture:**
```
Microcontroller → I2C → PCA9685 → servo control signals
```

**Important:**
- The PCA9685 does not provide the required servo power by itself
- The servos require a separate suitable power supply
- Controller ground, servo driver ground and servo power ground must be connected correctly

---

## V0.1 Minimum Build

### Required Components

- Existing ESP8266
- One TTP223 touch sensor
- WS2812B LED ring
- KY-006 passive buzzer
- One MG90S or SG90 servo
- Breadboard
- Jumper wires
- USB power for the ESP8266
- Separate suitable power for the servo

### First Target

```
touch → faster LED heartbeat → short buzzer sound → small servo movement → return to IDLE
```

---

## Not Required Yet

**Do not purchase yet:**
- Full humanoid servo set
- Final battery pack
- Raspberry Pi
- Jetson
- Final display
- Final speaker system
- Final humanoid body
- Walking hardware

**Important:** These parts should be selected only after the previous prototype stage works.
