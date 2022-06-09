# Basic-Motor-PWM-Speed-Control-With-555IC

![image](https://user-images.githubusercontent.com/19898602/172757889-180fbe37-14f6-4671-8b05-30a6bb4af506.png)


This project is about, controlling a fan using 555IC with PWM. PWM is controlled with a potentiometer. 

I drove a fan but you can use it for a DC motor. The circuit has a back-emf diode. 

I did this project using a prototyping board but if you want to produce the PCB, I will share the Gerber files too.

# Features

> Input has a 500mA fuse for protection.

> PWM is controlled with a 10k potentiometer

> Min. duty-cycle limiting at %25

> 1.5kHz PWM frequency.

> 1A@12V input supply.

> On/Off Switch.

> Back-emf diode for the motor.

> 350mA max @ 12V fan.


I selected these features but you can change input power, minimum duty-cycle value, or frequency depending on your motor power. I will show you later.

Hi everyone! Today I came to you with a basic project. I made this project a simple and cheap solution for soldering fume filters. Whenever I try to solder, fumes always follow me and I don't want to breathe it anymore! And I want you guys to don't breathe those fumes too.




# Circuit Material List

> 1xTLC555

> 1xIRF3710ZPBF

> 1x12V Fan

> 1x500mA fuse

> 1xOn/Off switch

> 1xDC Power Jack

> 4xSchottky or Standard Silicon Diodes

> 2x2.2uF, 1x1uF, 2x100nF, 1x10nF capacitors

> 1x10k Pot

> 1x3.3kOhm, 1x2kOhm, 1x1.2kOhm resistors

> At least 5x5cm Prototyping board

> Any adaptor plug above 500mA @12V


# Mechanic Material List

If you want to make a box too, I will share the STL files.

> Circuit protection box

> Some support materials for holding the fan

> 2 sides tape

> Some screws and nuts

As you can see in the photos above, a flexible, I guess aluminum material holds the fan. I found it in an old desk lamp.


# Desingning the Schematic

![image](https://user-images.githubusercontent.com/19898602/172758411-e2d0a347-b470-44d7-ab09-acb2992ee1c3.png)


# How Does This Circuit Work?

This circuit is working on the astable mode. In this way, we can simply adjust the C3 capacitor charging and discharging time with a 10k pot. D1 and D2 diodes block one side of the currents on the pot. R3 resistor is used for the limiting minimum duty-cycle value. 

We need to have a minimum value because the fan can't work under the 3V. So for the 12V input, the %25 duty-cycle is equal to the 3V. The C4 capacitor is not necessary but you can use it for the line regulation. The D4 diode is for back-emf protection. In this way, you can use any DC motor. 

The Q1 MOSFET is completely adequate. It can handle 100V and 49A!. If you want a more compact circuit, you can change it with another MOSFET that has fewer ampere value. So that, the size will be much fewer too. I used the F1 fuse because the circuit is plugged into the outlet. 

If any problem with the adapter, the fuse popped up and protects the circuit.


# PWM Frequency Calculation

1.5kHz works like charm. But under 20kHz can cause some audible noise. 1.5kHz has some audible noise too but it doesn't bother me. If you want to increase the frequency, you can choose any frequency under the table.

With the minimum %25 Duty cycle value;

2kHz → 50nF

3kHz → 35nF

5kHz → 20nF

10kHz → 10nF

15kHz → 7nF

20kHz → 5nF

By using TLC555 and IRF3710, you can increase the frequency 52kHz. But I am not suggesting it. Because discharging time getting too long according to the frequency. If you want to calculate your own frequency value, you can use this formula.

R3 = (Dmin * RPOT)/(1-Dmin) → Dmin: Minimum duty-cycle value.
f = 1/(0,693*(R3+RPOT)*C)


# MOSFET Gate Resistor Value Calculation

t first sight, it looks kinda difficult I know. But actually, it is just a simple capacitor theory. 
The capacitor is charged through the R1 resistor and discharged through the R1 + R2. If you add a diode parallel to the R1, it just discharged through the R2. 
TLC555 max. output current is 10mA. We have to choose the R1 value with respect to the 10mA.


R1 = Vo/Io → Vo is the out voltage of the 555IC and Io is the max. output current of the 555. 12V/10mA = 1.2kOhm

If we didn't use a diode parallel to the R1, the capacitor will discharge R1 + R2. The total resistance can be calculated like this.

R2 = (1-Dmax) / (-ln(Voff/Vout)*Cg*f)
Dmax: Maximum duty-cycle value
Voff: Turn off voltage of the MOSFET
Vmax: Output voltage of the 555
Cg: Gate capacitance of the MOSFET
f: Frequency

![image](https://user-images.githubusercontent.com/19898602/172758676-9900ad9c-5722-4398-9dd8-4dca4521e7bd.png)
![image](https://user-images.githubusercontent.com/19898602/172758694-f53caaf1-d116-48e3-8c06-a37fd691c78e.png)


# Soldering

![image](https://user-images.githubusercontent.com/19898602/172758733-09ed4813-52d9-4c71-93f7-6d3fb2b20f8b.png)
![image](https://user-images.githubusercontent.com/19898602/172758740-c87b529b-95e7-4b2c-9e9a-ff0a36754d38.png)


I used SMD versions of some diodes and capacitors. In this way, they can allow you to use both sides of the board. DC power jack's legs are bigger than the holes. Before you start soldering, drilling the adequate size for the jack makes your job easier.

![image](https://user-images.githubusercontent.com/19898602/172758784-d5f2f6a9-6359-43b9-83e6-6fdf8a1bcc1b.png)
![image](https://user-images.githubusercontent.com/19898602/172758793-81891de3-f6c9-41ca-b897-f88e157cf754.png)

I have design circuit and PCB in [easyEDA](https://easyeda.com/) and ordered PCB from [JLCPCB](https://jlcpcb.com/IAT )

This is the link of [PCB editabl file](https://oshwlab.com/sharmaz747/multipurpose-pcb)

Yes PCB are the heart of the electronics based project usually we hesitate to try custom PCB and opt to homemade solutions

like breadboard or Zero PCB earlier I also was in the same boat, I hesitate to try custom PCB my belief was they are much expensive.

but then I came to know about [JLCPCB.COM](https://jlcpcb.com/IAT) and I was totally surprised how low price PCB's are they offering 

there PCB quality is best in market, now I always go with PCB for my project and [JLCPCB.COM](https://jlcpcb.com/IAT) is my trusted 

If you planing to order any PCB for your projects so you can consider [JLCPCB.com](https://jlcpcb.com/IAT) because

I always prefer [JLCPCB.com](https://jlcpcb.com/IAT) for my PCB needs, [JLCPCB.com](https://jlcpcb.com/IAT) have best deals for their customers
$2 for 1-4 Layer PCBs, free SMT assembly monthly.

If you seriously need quality PCB quickly in your hand then you must have to try JLCPCB PCB manufacturing service. They have Special offer of $2 for 1-4 Layer PCBs, free SMT assembly monthly. If new user signup today from this link [JLCPCB.com](https://jlcpcb.com/IAT) you will get welcome coupons from JLCPCB.


![image](https://user-images.githubusercontent.com/19898602/159014034-3c9a50c3-61c3-40d2-836d-9cadc2317d33.png)
![image](https://user-images.githubusercontent.com/19898602/164385177-de123350-4a1f-4d0f-9f38-68ed7dbd5a9f.png)



SMT Assembly service of [JLCPCB.com](https://jlcpcb.com/IAT) is cherry on top now get your PCB fully assembled and save your time and money
Select components for your PCB from there Parts Library of 200k+ in-stock components
they are offering $30 valued New User coupons  & $24 SMT coupons every month
$8.00 setup fee, and $0.0017  per joint

Now no need to order components separately for you PCB and get free from stress of soldering them on PCB just try PCB SMT assembly service and get you PCB with components pre assembled and ready for the project


👉 Try PCBA service of [JLCPCB.com](https://jlcpcb.com/IAT) and save your time and money, get PCB ready for project, 200K+ components in library of [JLCPCB.com](https://jlcpcb.com/IAT) as well as 3rd party         parts to choose from. 
    Assembly will support 10M+ parts from Digikey, mouser
    
👉 $30 valued New User coupons 

👉 $24 SMT coupons every month


For more detials & offers please visit [JLCPCB.com](https://jlcpcb.com/IAT)





