# xpPresepe - Presepe lights-controller eXPerience
A modular presepe lights controller.

![overview](images/presepe-controller.jpg)

The idea is to make a light controller with the following specs:
- No MCU or digital ICs, only use of analog components
- Modular approach via BUS
- Power voltage supply between 12 and 24 VDC, with no effects on timings and thresholds
- Simulation of the phases of the day: sunrise, day, sunset, night
- Fade in/out effect on the output lines
- Tremolo effect for simulate stars
- Fire-light effect simulation
- Driving of low-current led strings, synchronized with phases of the day or a combination of them


## Logical Modules

### Sawtooth wave generator
### Daily-phase triggers generator
### LFO square wave generator
### BUS and Backplane
The BUS has the following lines:
* Power lines :
	* +Vcc
	* Gnd
* Phase Triggers lines :
	* tA - sunrise-phase trigger
	* tG - day-phase  trigger
	* tT - sunset-phase trigger
	* tN - night-phase trigger
* Wave lines :
	* S - sawtooth wave
	* lfo - 15Hz square wave
	
### Daily-Phases output lines
### Stars output lines
### Fire-lights output lines
### Nosync output lines


## Physical Boards

### Main board
[main-board](main-board) implements the sawtooth wave generator, the daily-phase triggers generator, the lfo generator and the BUS-backplane.

### Daily-Phases Lines Board
[phases-lines-board](phases-lines-board) implements quad current driven output lines, configurable fade in/out effect,
synchronization with phase-triggers or a combination of them, and flickering effect.

### Fire-lights Lines Board
todo

### Nosync Lines Board 
todo


## About
Author : Alessandro Fraschetti (mail: [gos95@gommagomma.net](mailto:gos95@gommagomma.net))


## Credits:


## Licence
The [MIT license](LICENSE) posted in the main repository directory is applied to all the eXPerience stuff.
You are free to use them for any purpose, just try to give credit in the documentation of your project.