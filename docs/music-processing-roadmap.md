# Huggy Music Processing Roadmap

## Music V0.1 – Recording and Emotional Logging

The first version does not need advanced music analysis.

Main goals:

* record evening piano practice as an audio file;
* save the date and time of the practice;
* store what piece was played;
* store what Kristóf felt during the practice;
* connect music practice to Huggy's journal.

Example:

```text
2026-07-12
Piece: improvised evening piano
Feeling: longing, calm sadness, hope
Note: played softly after thinking about the Mexican girl
```

## Music V0.2 – Basic Audio Feature Detection

Huggy starts detecting simple audio features from recordings.

Main goals:

* detect recording length;
* estimate loudness;
* detect quiet parts and silences;
* estimate rough tempo;
* measure changes in volume.

Possible detected features:

* duration;
* average loudness;
* dynamic range;
* silence ratio;
* rough tempo;
* loudness changes over time.

## Music V0.3 – Basic Mood Estimation

Huggy starts making simple mood guesses from the music.

Possible mappings:

* soft and slow playing → calm or sad mood;
* strong and dynamic playing → intense emotion;
* many pauses → reflective, hesitant, or longing mood;
* very quiet playing → fragile or tired emotional state;
* more movement and volume → stronger emotional release.

The goal is not perfect music understanding.

The goal is for Huggy to notice simple emotional patterns in the way Kristóf plays.

## Music V0.4 – Reflective Responses

Huggy starts responding to music practice in a personal way.

Example responses:

* “You played more softly today than yesterday.”
* “There were many pauses, as if you were holding something back.”
* “This part felt stronger than the rest of the practice.”
* “The ending was quieter, almost like you did not want the feeling to disappear yet.”

Huggy should connect the music to the emotional journal carefully, without overanalyzing.

## Music V1.0 – Live Listening and Physical Reaction

Huggy listens live through a microphone and reacts physically to piano practice.

Main goals:

* listen to piano practice in real time;
* detect volume and silence while the user plays;
* make LEDs breathe with the music;
* move gently during softer or more emotional parts;
* connect the music mood to Huggy's internal state.

Example future behavior:

`piano sound → audio features → mood estimate → LED breathing → small servo movement`

At this stage, Huggy does not only talk about music.

Huggy listens to it, reacts to it, and becomes part of the room.
