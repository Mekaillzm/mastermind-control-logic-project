# Simulation Overview
There are two players: the game master and the the guesser.

The game master creates a hidden code with an array of four LEDs. Each LED can have upto eight colors.

The guesser then has nine tries to guess the hidden code. They must guess a colour for each LED and press a button to submit their final answer.

A separate array of four green LEDs lights up to indicate whether they are correct or not. For instance, if the third LED in their guess is correct, but the others are wrong, then only the third green LED will light up.

Once all four LEDs are green, the guesser wins, otherwise, the game master wins.

# Important Notes & Assumptions

This folder contains the most recent simulation that was implemented practically.

The real life project differed slightly due to the availablility of ICs and parts.

Changes:
-Proteus has numerous restrictions regarding clock pulses and signals that do not exist in real life. E.g. a button or a button with a debouncer cannot power the clock input of an IC directly. This has been tested to work in real life.
So, all buttons have been replaced by logic states for simulation purposes. They should be clicked twice for one clock pulse.

-Dials have been shown as variable resistors for simulation purposes. In real life, the dial will be placed on the variable resistor, and it can be turned for easy color control.


-Proteus has numerous restrictions regarding clock pulses and signals that do not exist in
real life. E.g. a button or a button with a debouncer cannot power the clock input of an IC
directly. In the practical setup, the submit button was made with an RC-filter and

-Dials have been shown as variable resistors for simulation purposes. In real life, the dial will
be placed on the variable resistor, and it can be turned for easy color control

-The MOSFETs in the simulation were replaced by op-amp comparators in the real setup. Due to the great number of ICs and LEDs, there was a sizable voltage drop from the output of the flipflops, such that it was no longer suitable for the ICs. Thus, the comparators were used to push the lower voltages back up to 5V (HIGH) or 0V (LOW).

-Resistance values may have differed in the practical setup.

Resistances (practical):
Vref: 5.6 kOhm and 2.1 kOhm
pull-back resistors: 5.6 kOhm



# The Four Circuits

The logic consists of four indepdendent circuits:
-game master logic
-guesser logic
-Answer checking logic
-Tries counter logic

# Color selection

To select an LED and set its color, the player should do the following:

-Press the cycle button, to move between LEDs
E.g. if they are on the first LED in the row, they can press the cycle button twice (or logic state four times) to get to the third LED.

Initial: LED 0

Color Cycle pressed: LED 0 -> LED 1

Color Cycle pressed again: LED 1 -> LED 2


-After the LED has been selected, the player can turn the three dials to choose the color.
There are 3 colour dials (RGB), with 2^3 = 8 total color options available by mixing and matching them.

A dial is on when its resistance is above the 50% threshold.

Dial 1: RED
Dial 2: GREEN
Dial 3: BLUE

E.g. if you want magenta, turn RED and BLUE on, and GREEN off.

RED  Green  Blue  Resulting Color
OFF  OFF    OFF      Blue
OFF  OFF    ON       Blue
OF   ON     OFF      Green
OFF  ON     ON       Cyan (Blue-Green)
ON   OFF    OFF      Red
ON   OFF    ON       Magenta (Purple-Pink)
ON   ON     OFF      Yellow
ON   ON     ON       White (All colors combined)

# Game master logic

The following interface is available:
(All buttons have been replaced by logic states for simulation purposes. All dials have been replaced by variable resistors.)

-LED Cycle button: used to change the LED colour
-Reset Button: Resets the circuit back to its initial state
-Red color dial: when increased above 50%, the color mixer selects RED
-Blue color dial: when increased above 50%, the color mixer selects BLUE
-green color dial: when increased above 50%, the color mixer selects GREEN

# Guesser logic

The following interface is available:
(All buttons have been replaced by logic states for simulation purposes. All dials have been replaced by variable resistors.)

-LED Cycle button: used to change the LED colour
-Submit button: Pressed to submit the guess, and increment the attempts counter by 1
-Red color dial: when increased above 50%, the color mixer selects RED
-Blue color dial: when increased above 50%, the color mixer selects BLUE
-green color dial: when increased above 50%, the color mixer selects GREEN

# Answer checking logic

The following is available: four LEDs that show when the player is right or wrong.

e.g.
LED 1: ON
LED 2: OFF 
LED 3: ON 
LED 4: OFF

The first and third LEDs have the correct colour.

# Tries counter logic

This shows a 7-segment BCD display indictating how many tries the player has taken so far. E.g. 4 means 4 tries have been done, and 9 - 4 = 5 tries are left.




