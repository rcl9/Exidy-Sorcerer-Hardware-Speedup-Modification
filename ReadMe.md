 # How to Speed up the Exidy Sorcerer I from 2Mhz to 3.16Mhz

This repo describes a hardware modification I made to my Exidy Sorcerer in 1981 to increase its
clock rate from 2Mhz to 3.16Mhz, switchable.

Before we start cutting traces I must mention that the increased speed will not work with cassette or disk 
operations but is fine when the switch is in normal mode. You must also have 300ns or faster memory installed. This 
circuit is based on the model one and may need changes for the Sorcerer model II.

<div style="text-align:center">
<img src="/Images/figure-2.jpg" alt="">
</div>

## Operation

With reference to figure # 1, the main 12 Mhz clock frequency in a normal Sorcerer is divided by three at IC 5B which goes onto a divide-by-two counter to bring the final Z80 CPU clock rate to the slower 2.106 Mhz.

<div style="text-align:center">
<img src="/Images/figure-1.jpg" alt="">
</div>

With the new speed-up modification, the divide-by-three sec:tion has been replaced with a divide-by-two counter altering the final CPU clock to become 3.15 Mhz.

As for the new circuit, IC 74LS74 acts as a de-bounce mechanism for the switch , allowing the two different clock rates to be switched back and forth without a system crash.

Pin 1 of the 74LS00 NAND gate (Z7A) has the divided-by-three clock from the main circuit
board and pin 5 has our new divided-by-two clock. The output of the
D-type flip flop, selected by the switch, determines which Nand gate to
turn on. Thus sending the appropriate clock frequency onto the final
divider of the main IC board and then to the Z80.

The main video timing clock is not touched in this setup so the screen
accesses are normal.

## Installation

You will need a wire wrapping pencil, long nose pliers, a wire cutter, a drill, low wattage soldering iron, a sharp knife and silver solder.

First, remove the keyboard from the computer chassis by taking out the five screws found on the front and rear of the computer.

We will now drill a hole for the miniature switch. If 
the switch is too large the keyboard cover will not sit 
correctly on the computer chassis. So be sure to buy a 
miniature switch. The most suitable location for it is the 
front chassis lip between the two metal screens, and between 
the IC board and the plastic keyboard rest. See the diagram 
for location. Drill the hole,install switch and tighten the 
bolt. You may want to check to see if the keyboard touches 
the switch by placing the cover back on for a trial fit.

For the following wiring steps, refer to the diagram for wire placement.

- Locate ICs 5A and 6A. Then locate the trace that runs 
between pins 2 and 3 of 6A and extends towards 5A where it 
cuts through the board to the opposite side. Take the X-acto 
knife and cut away the trace leaving enough to allow 
soldering of wires to both sides later. 

<div style="text-align:center">
<img src="/Images/Ref-1.jpg" alt="" style="width:70%; height:auto;">
</div>

- Take a 4.7k resistor and solder one end to the left 
side of the switch lug leaving the centre lug free for now. 
 Next, take the other 4.7k resistor and solder one end to 
the right side of the switch. Keep the resistors horizontal 
so the keyboard will not interfere with their operation.

- Now cut and bend the free ends of the two resistors so 
that they are joined. Then solder the ends together. Also 
solder a piece of wrapping wire from pin 14 of IC 10A to the 
ends of the two resistors just soldererd together.

<div style="text-align:center">
<img src="/Images/Ref-2.jpg" alt="" style="width:70%; height:auto;">
</div>

- Take one 14 pin standard IC socket and bend up all the 
pins on a 45-50 degree angle except pins 7 and 14.

- Piggyback this socket atop IC 7A and solder pins 7 and 14 of the socket to pins 7 and 14 of IC 7A. Make sure none 
of the bent pins touch the pins of 7A. This socket will now be called Z7A.

<div style="text-align:center">
<img src="/Images/Ref-3.jpg" alt="" style="width:70%; height:auto;">
</div>

- Now take the other 14 pin socket and bend up all pins except 1, 4, 7 and 14. You may refer to the diagram for 
pinouts if you don't know how an IC chip is numbered. Piggyback and solder this socket to IC 9A. Pins 1, 4, 7 and 
14 will be soldered to the corresponding pins of IC 9A and the rest are bent up. This socket is now called Z9A.

<div style="text-align:center">
<img src="/Images/Ref-4.jpg" alt="" style="width:70%; height:auto;">
</div>

- Connect the right side of the trace cut (where the trace goes through the board to the opposite side) by soldering it to pin 1 of Z7A.

- Connect the left side of the trace cut (just before the trace goes between pins 2 and 3 of 6A) by soldering it to pin 8 of Z7A.

- Connect the centre lug of the switch to pin 7 of 10A. This completes the switch installation.

- Connect pin 6 of 1B to pin 5 of Z7A.Then connect pin 3 of Z7A to pin 9 of Z7A (on the same socket).

- Connect pin 6 of Z7A to pin 10 of Z7A.

- Connect pin 13 of Z9A to the left side of the switch (and on the same lug as the 4.7k resistor is soldered to).

- Again connect pin 10 of Z9A to the right side of the switch (on the same lug as the 4.7k resistor is soldered to).

- Connect pin 9 of Z9A to pin 2 of Z7A.

- To complete the circuit, connect pin 8 of Z9A to pin 4 of Z7A.

Now go over the modification and check for solder bridges or wrong connections.

Insert the 74LS00 into socket Z7A and the 74LS74 into Z9A. Plug in the computer and turn it on. Any smoke? No - that's good. Now see if the chips are getting hot. If so, unplug the computer and check the circuit for shorts.

Put the keyboard back on and don't forget to put the clip on the DIP plug.

Insert the Basic Rom-Pac and turn on the computer. If the sign on message fails to appear or the system 
crashes, flick the switch to the opposite side and turn the computer on again. The computer will normally require the 
switch to be placed in the normal mode upon initialization.

Type in listing 1. Get a stop watch and run the program, timing it at the same time. If the time is 16 
seconds, put a label on the computer beside the switch in the direction the lever is pointing to. Label this as 
'NORMAL'. Now flick the switch over and repeat the above. Your watch should read 11 seconds. If not, either your 
memory is too slow, the circuit is wired wrong or the Z80 will not handle 3.16 Mhz.

Put a label with 'FAST' on it at the side the switch is now pointing to.

There are some side effects of the modification on the Sorcerer. If you fill the screen with characters and turn on 
the high speed switch, there is some screen flicker towards the right side of the screen. Also the keyboard may bounce 
if you are a fast typist.

*Warning* Casstte and disk I/O will not work reliably at the higher speed. Remember to turn off the high speed mode before saving or loading programs. 

Now load in a slow machine lanquage game and run it at high speed. WOW what an improvement!

## Parts List

|Quantity | Description |
| :-----: | :---: |
| | |
| 1 | Miniature SPDT toggle switch (Radio Shack # 275-8069) |
| 2 | 14 pin standard IC sockets  |
| 2 | 4.7k , quarter watt resistors  |
| 1 | 74LS00 NAND gate |
| 1 | 74LS74 D-TYPE flip flop |
| 1 | Roll of wrapping wire |

## Listing # 1

10 PRINT "Start"

20 FOR I = 1 TO 10000

30 NEXT I

40 PRINT "Finished"
