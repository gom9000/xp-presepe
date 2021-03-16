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
A signal that varies linearly, whose frequency corresponds to the whole day-presepe.
To produce the ramp, a constant current generator is used which linearly charges a capacitor,
and a comparator with hysteresis that regulates the maximum charge voltage of the capacitor, and the relative discharge.

### Daily-phase triggers generator
Passing the ramp signal through 4 voltage window-comparators, the ramp is divided into 4 periods,
from which to obtain the 4 trigger signals of the related phases of the day-presepe.

### LFO square wave generator
Produce flickering light to simulate stars.
It is implemented by an astable multivibrator, with buffered output to increase the fan-out.

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

### Daily-Phase light fade in/out effects
Gradually turns on and off the led strings linked to a phase of the day-presepe.
A current-source generator is used to charge a capacitor, the charge of which is controlled by a voltage comparator and the phase-trigger.
When the trigger is deactivated by means of a diodes switch, the capacitor discharges on a current-sink generator.
Starting from the rectangular trigger signal, a trapezoid-shaped voltage signal is obtained.

### Voltage to current converter
A current signal is required to drive the LED strings. An emitter-follower and current mirrors serve as a converter and line doubler.
The trapezoid-shaped voltage signal is transformed into a trapezoid-shaped current signal.

### Stars-light effect
Mixing toghether the trapezoidal and lfo voltage signals, the result is a serrated signal that emulates the tremolo light of the stars.

### Fire-light effect
todo


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