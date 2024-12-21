# Danfoss valves

The original Danfoss solution was a 3-wire installation.

The danfoss valve was the original integrated autosteer valve. They’ve been used by Deere, Agco, CNH, etc.

It would have been the easiest way for a tractor manufacturer to add an autosteer valve, the valve is built right into the steer motor. No additional plumbing is required. If you have one of these, you do not need a Cytron, but your board must have the TC4227 (PCB4.1) chip installed. JLCPCB will fit these to version 4 builds if they're in stock at time of ordering them.

Instead of sending a typical left or right PWM signal down separate channels, what they do instead is energise (or unlock) the Danfoss with the right channel and send a varying PWM signal down the left channel, where 50% is straight ahead, approx 15-25% is full left and 75-85% is full right (this is part of the safety systems to prevent shorts and such like causing unintended movement). Saying it again, the LEFT output therefore steers both left and right. Gnd must also be supplied of course. You should not power the lock via a relay, but drive from the board.

![image](https://github.com/AgHardware/Boards/assets/9885921/fd9f5ca7-6f22-488e-9ea9-7322a527bd9a)

![image](https://github.com/AgHardware/Boards/assets/9885921/23759834-ba61-48fe-b2d6-a04719393e45)

To use this configuration, your machine must have this kind of valve, you need the chip on the board and you need the jumpers positioned on the board at (picture).

![image](https://github.com/AgHardware/Boards/assets/9885921/6a991ca5-85da-485e-8449-988ef3b88aa0)

Sample Danfoss plug guide, but check with your module!!

![image](https://github.com/AgHardware/Boards/assets/9885921/4f40824d-e627-428c-8454-92eee865eb74)

## Identifying a Danfoss valve

![image](https://github.com/AgHardware/Boards/assets/9885921/de5d0c34-ec79-4492-9b94-153e72171d45)

![image](https://github.com/AgHardware/Boards/assets/9885921/cbde0fc3-4590-4c7e-8991-0f065673f266)

![image](https://github.com/AgHardware/Boards/assets/9885921/32c566ba-3bbd-4e9e-a87e-0e74f699f262)

You can find the 4-pin connector on the [Connectors](https://github.com/AgHardware/Boards/wiki/Connectors) page
