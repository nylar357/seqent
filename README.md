# Techno Terminal Sequencer Commands

Welcome to the Techno Terminal Sequencer. This environment uses a command-line interface to control a 10-piece, 808/909-style synthesized drum kit. 

Below is the complete documentation for every available command, required syntax, and reference tables for instruments and tuning.

## 🎵 Playback Controls

Control the main engine and timing of the sequencer.

* **`play`**
  * **Description:** Initializes the Web Audio context (if suspended) and starts the lookahead scheduler loop.
  * **Syntax:** `play`
* **`stop`**
  * **Description:** Halts the scheduler loop, stopping all sequencing and audio generation.
  * **Syntax:** `stop`
* **`bpm [value]`**
  * **Description:** Sets the global tempo of the sequencer.
  * **Syntax:** `bpm 140`

## 🧮 Euclidean Sequencing

Generate static, mathematically spaced rhythms.

* **`set [instrument] [steps] [pulses]`**
  * **Description:** Generates a static Euclidean rhythm and assigns it to an instrument. It distributes the `pulses` as evenly as possible across the total `steps`. Overrides any Cellular Automata running on that instrument.
  * **Example:** `set kick 16 4` *(A standard 4-to-the-floor kick drum)*
  * **Example:** `set snare 16 5` *(A syncopated 5-hit rhythm over a 16-step bar)*

## 🧬 Cellular Automata Sequencing

Generate evolving, generative rhythms using Wolfram rules.

* **`ca [instrument] [rule]`**
  * **Description:** Injects a dynamic Wolfram Cellular Automata algorithm into an instrument track. Starts with a single pulse and mathematically evolves to the next generation every time the 16-step loop restarts.
  * **Example:** `ca hihat 30` *(Applies Rule 30 to the closed hi-hats)*
  * **Example:** `ca clap 90` *(Applies Rule 90 to the claps)*

## 🎛️ Audio Synthesis Tuning

Shape the sound of your analog-style drum kit in real-time.

* **`tune [parameter] [value]`**
  * **Description:** Alters the mathematical properties of the Web Audio API synthesis nodes.
  * **Example:** `tune kickdecay 1.5`
  * **Example:** `tune hatfilter 10000`

## 🛠️ Utility

* **`help`**
  * **Description:** Prints a quick-reference list of commands and available instruments directly to the terminal screen.
  * **Syntax:** `help`
* **`clear`**
  * **Description:** Clears the terminal output screen.
  * **Syntax:** `clear`

---

## 📋 Reference Tables

### Available Instruments
Use these IDs with the `set` and `ca` commands.

| ID | Instrument | Description |
| :--- | :--- | :--- |
| `kick` | Bass Drum | 909-style pitched sine sweep |
| `snare` | Snare Drum | Triangle tone + highpass noise |
| `clap` | Clap | 808-style multi-spike bandpass noise |
| `chh` | Closed Hi-hat | Short highpass noise burst |
| `ohh` | Open Hi-hat | Long highpass noise burst |
| `toml` | Low Tom | Low pitched sine sweep |
| `tomm` | Mid Tom | Mid pitched sine sweep |
| `tomh` | High Tom | High pitched sine sweep |
| `ride` | Ride Cymbal | Inharmonic metallic ring |
| `crash` | Crash Cymbal | Swept inharmonic metallic crash |

### Available Tuning Parameters
Use these keys with the `tune` command.

| Parameter | Default | Description |
| :--- | :--- | :--- |
| `tempo` | 130 | Global BPM |
| `kickpitch` | 120 | Kick start frequency in Hz |
| `kickdrop` | 45 | Kick target drop frequency in Hz |
| `kickdecay` | 0.5 | Kick tail length in seconds |
| `snarepitch` | 200 | Snare triangle body frequency in Hz |
| `snarefilter` | 1500 | Snare noise highpass cutoff in Hz |
| `clapfilter` | 1500 | Clap noise bandpass center in Hz |
| `hatfilter` | 8000 | Hi-hat noise highpass cutoff in Hz |
| `tomlow` | 80 | Low tom frequency in Hz |
| `tommed` | 120 | Mid tom frequency in Hz |
| `tomhigh` | 160 | High tom frequency in Hz |
| `ridedecay` | 1.2 | Ride cymbal ring length in seconds |