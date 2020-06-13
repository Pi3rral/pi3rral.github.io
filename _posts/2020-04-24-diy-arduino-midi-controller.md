---
layout: post
title: DIY Arduino Midi Controller
date: '2020-04-24T15:00:00.000-08:00'
author: Pi3rral
tags:
- midi
- arduino
- diy
img: midi/channel.jpg
---

# Github Repository

<https://github.com/Pi3rral/midi-controller>

# Arduino MIDI Foot Controller

Simple MIDI foot controller made with an arduino and an external 3 buttons footswitch (type Digitech FS3X).

## Features

- Input Jack for a 3 switches controller (type Digitech FS3X)
- Output Jack MIDI TRS-A
- OLED Display


## Schematic

![Schematic](/assets/img/midi/MIDIControllerSchematic.png)

## Photos

![outside](/assets/img/midi/outside.jpg) | ![inside](/assets/img/midi/inside.jpg)
---------|--------
![channel_select](/assets/img/midi/channel_select.jpg) | ![footswitch](/assets/img/midi/footswitch.jpg)

## Usage

### MIDI Channel

The controller is sending Program Change (PC) instructions on MIDI Channel 1.

### Footswitch

#### MODE Button

Pressing MODE button is actually sending the Program Change (PC) to the MIDI output.
It will display in big the PC number its sending, and remove the small one at the top right of the screen.
Selecting the PC number is done by pressing UP and DOWN buttons.

#### UP/DOWN Buttons

Pressing UP or DOWN button will define which PC send when we will press the MODE button.
OLED will display in big the next PC, while displaying the current PC in small at the top right of the screen. 

WARNING: UP or DOWN will NOT send the PC instruction. It will just select it for pressing MODE.


## Building With `arduino-cli` To An Arduino Nano Clone

https://arduino.github.io/arduino-cli/

### Setup

```bash
brew install arduino-cli
arduino-cli core update-index
arduino-cli core install arduino:avr
```

### Build

```bash
arduino-cli compile --libraries libraries midi-controller
arduino-cli compile --fqbn arduino:avr:pro --libraries libraries midi-controller
```

### Upload

Find port where board is connected
```bash
arduino-cli board list
```

Upload
```bash
arduino-cli upload -p /dev/cu.usbserial-1420 --fqbn arduino:avr:pro  midi-controller
```

