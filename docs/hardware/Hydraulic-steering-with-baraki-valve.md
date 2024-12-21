# Motor? Nah - hydraulic please!

This still needs Cytron MD13S :) but we'll move valves instead of motors

So, if your system is compatible, you can likely steer it directly without a motor turning the steering wheel.

Motor settings are follow:

  * Proportional gain - depends on the size of the piston:
    * 15 for small tractors
    * 40 for the big ones
  * The maximum Limit maxPWM - depends on the size of the piston 100-180
  * The minimum to move minPWM is 38-40

## How to choose a valve?
There are a few kind of valves depending on the Orbit installed. These are available in the shop: https://www.agopengps.pl/en/shop-1?currency=EUR

Take a look at your Orbitrol: 
  * 4 hoses then you'll need an [OC valve](https://www.agopengps.pl/en/product-page/zaw%C3%B3r-hydrauliczny?currency=EUR) and will be connected between the pump / steer lines.
  * 5 hoses will be an LS system and needs an [LS valve](https://www.agopengps.pl/en/product-page/zaw%C3%B3r-hydrauliczny-do-uk%C5%82adu-ls) with "Tee" connection and will be connected parallel to the P / T lines and between the LS / steer lines.
  * !!! some of the tractors require special valves, for example: 
    * Fendt (static) 
    * [John Deere 4XXX](https://discourse.agopengps.com/t/hydraulic-valve-assemblies-for-every-tractor-for-every-type-of-hydraulic-system/8011/586?u=bgunics) 
    * CASE Quadtrack (90L) require special valves !!! Double check on these. 

The valve flow depends on the tractor size. 150-200HP tractors will likely need 60liter. The forum might have tips from baraki. If unsure add a note about your tractor to the order!

https://discourse.agopengps.com/t/hydraulic-valve-assemblies-for-every-tractor-for-every-type-of-hydraulic-system/8011

## The valve itself:
![image](https://github.com/AgHardware/Boards/assets/9885921/bdbf1121-942f-4c91-bf7d-98d6dff784a7)
Engineering drawings:
**OC**

![image](https://github.com/AgHardware/Boards/assets/9885921/018ac8c2-2465-481a-8f51-42889aeed5eb)

Explanation: [Credit goes to Commonrail](https://discourse.agopengps.com/t/hydraulic-valve-assemblies-for-every-tractor-for-every-type-of-hydraulic-system/8011/578?u=bgunics)

* 2 is a logic valve, it basically makes a small LS closed centre system inside this valve block for the autosteer. This valve will keep the P line a few bar higher than the internal LS line (in other words a few bar higher than what is needed to operate the wheels at the current time)

* 1 is a relief valve used to limit the maximum pressure for the steering, when this valve is tripped the LS line can’t go any higher and the valve 2 will let the oil out the T port

* The pressure sensor is connected to the valve block T line, this line is connected to the P port of the orbital and because it is open centre the oil free flows to tank. But when you turn the steering wheel the pressure in this line rises as oil is needed to turn the wheels, because the orbital steering lines are blocked this pressure rises quickly and the sensor trips to tell autosteer to stop steering


**LS**

![image](https://github.com/AgHardware/Boards/assets/9885921/4ed9787a-88ea-4ae1-927d-84cdc8598395)

Special valve for Fendt:
![image](https://github.com/AgHardware/Boards/assets/9885921/ba7ba07c-2550-43c9-b827-23c8ff0f6c6e)

## Installation
Electrical connection(s)
![image](https://user-images.githubusercontent.com/3919203/230915183-16aebabc-b4a0-487c-9a3e-4448b1678138.png)
Theoretically the FET should be capable to handle the power to lock the valve. In practice we've seen smoke in some cases.
Best practice is to add a relay controlled by the Lock pin.


There are 2 kind of "pressure" check valves:
### Count type
The one with 2 pins needs to be connected between Ground and Pres/Rem connection. 
The sensor is a SUCO 166 416 0 31 063 NC

![image](https://github.com/AgHardware/Boards/assets/9885921/407c9fcf-10e7-4059-b96c-2a5085ae89c3)

The PCB jumpers must be configured as Remote. 

![image](https://github.com/AgHardware/Boards/assets/9885921/4ec669b7-f63b-4a76-a4b8-a60641b52426)

AgOpenGPS must be configured as "Turn sensor" with value as "1". (it only clicks once)

![image](https://github.com/AgHardware/Boards/assets/9885921/a88a438a-6db3-4946-85c8-2a0ccb78e643)

### Pressure type
The one with 3 pins uses an AMP Superseal 3pn 1.5 connector and requires 5V from PCB (WAS 5V could be used). 

The sensor is:
0606-25209-B-007 Pressure Transmitter 
0 bar - 250 bar 0.5-4.5V
Ratiometric NPT1/4 AMPSuperseal
1.5 17-4PH Stainless Steel Cell

![image](https://github.com/AgHardware/Boards/assets/9885921/e7c544e5-8a94-4225-b7f6-fef2aa5cfd45)


The PCB jumpers must be configured as Pressure. 

AgOpenGPS must be configured as Pressure with value accordingly.(~10% is equivalent as 0bar)

![image](https://github.com/AgHardware/Boards/assets/9885921/2ae88dcc-2c75-4a73-8e59-67506727f3d4)

pinout is:
 - pin1 -> signal
 - pin2 -> GND
 - pin3 -> 5V

[AgOpenGPS software configuration is explained in detail here](https://github.com/farmerbriantee/AgOpenGPS/wiki/04.-AgOpenGPS-Orientation#steer-configuration)


### Installation of LS valve
![image](https://user-images.githubusercontent.com/3919203/230915103-ab56d783-19a9-4b82-8bd2-45a6b643c42f.png)
![image](https://user-images.githubusercontent.com/3919203/230915283-89b5ac5b-df8e-4e53-945a-47ebc1b6e7a9.png)
![image](https://user-images.githubusercontent.com/3919203/230914923-55955d43-eb23-4d5b-8b24-802079a70226.png)

### Installation of OC valve
![image](https://github.com/AgHardware/Boards/assets/9885921/7315c9fb-2890-4194-94f9-c60e46234946)

# Installation example
Marek (maker of baraki valve) has a great set of pictures [here](https://photos.app.goo.gl/pQFi3ziAcnyhWgAR8) for installation on a Massey 5445

# Plugs that are of use

If you have the two-pin plug for left/right solenoids, you can use these (TE part 718-6867)  to connect:

https://uk.rs-online.com/web/p/automotive-connectors/7186867

![image](https://github.com/user-attachments/assets/a45c0b15-0e77-432b-b393-1c7915798630)

If you want to use 3-pin plugs for the lock valves that have the schotky diode built in, use these Molex part S28200TC310R):

![image](https://github.com/user-attachments/assets/354baf18-2bbf-4090-a650-92a374637acd)

https://www.kempstoncontrols.co.uk/S28200TC310R/Molex/sku/457859


