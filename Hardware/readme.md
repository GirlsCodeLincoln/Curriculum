# Overview

This semester we're going to use [Raspberry Pis](https://www.raspberrypi.org/) to do the following projects this semester.

* A Retro gaming computer.
* A music streaming service.

## Lecture 1 - A brief history of the Raspberry PI

## Lesson 1 - Unpack your Raspberry Pi & Setup

1.  Unpack your Raspberry PI. You will have (4) components. From left to right in the picture the case,
the Raspberry Pi itself with a heatsink, the power supply & the setup guide.
![raspberry pi package](https://i.imgur.com/NQ7T6qg.png)

2. Carefully peel back the blue plastic from the heatsinks. Apply the sticky side down to the two processors (The black chips) on the raspberry pi.
![blue plastic](https://i.imgur.com/sNtG2b6.png)
![plastic gone](https://i.imgur.com/oqBOovH.png)
![final with heatsink](https://i.imgur.com/xJucUEr.png)

3.  Watch [the video](https://www.canakit.com/pi-case) for installing the Raspberry Pi into the case.

4. Get a SD card from the teacher and plug it into the SD card slot on the Raspberry PI.
![raspberry sd card](https://i.imgur.com/rFfj3P5.jpg)

5. Plug in the power supply. Green/Red lights should come on 
![raspberry powered on](https://i.imgur.com/fvWyjcA.jpg)

6. Talk to the teacher to get a monitor so we can get the IP address of your Raspberry PI.

7. Open up your laptop, and open Putty. Fill in the IP Address from step 6 and click `open`
![putty window](https://i.imgur.com/p5JEHTk.png)

8. Login to the machine with the following credentials:
```
username: pi
password: raspberry
```

9. At the command line type in `sudo raspi-config`

10. Select `change user password and hit enter when prompted.

11. type in `girlsrule` in password and confirm password and then `ok` when the success box come sup.

12. Use the arrow keys to select `interfacing options` and press `enter`

13. Select `vnc` and press `enter` and select `yes`. When prompted type in `y`.

14. Once it has finished use the arrow keys to select `finish`.

15. At the command prompt type `sudo apt-get update`

16. at the command prompt type `sudo apt-get install lightdm` and then type in `y` when prompted.

17. Once it has finished installing type in `sudo rapsi-config`.

18. Once it has finished installing, select `boot options`.

19. Select `Desktop/CLI` and then `desktop autologin`.

20. Go back to the main screen and select `<finish>` when prompted to reboot select `<no>`

21. Type in `sudo apt-get install lxsession` when prompted type in `y`

22. Once it has finished type in `sudo shutdown -r now` 

23. On your laptop find the program called `vnc viewer` - it'll be under a folder called `real vnc` in the start menu.

22. Enter the IP address from step 6.

24. A box will come up with a warning, select continue.

25. If prompted enter the username/password below and select `remember password`.
```
username: pi
password: girlsrule
```

26. Congratulations! You are now logged into your Raspberry PI!

## Lecture 2 - What is apt-get? What's Raspbian?

## Lesson 2 - Obligatory Minecraft Installation

1. If you havent already, log into your Raspberry PI using RealVNC as detailed in steps 23-25 in Lesson 1.

2. Select the application button at the far bottom left then system tools -> lxterminal
![loonix terminal picture](https://i.imgur.com/2oNqpHz.png)

3. Type in `sudo apt-get update` and then enter.

4. Type in `sudo apt-get -y install minecraft-pi`.

5. Go to the applications icon at the far left then games -> minecraft
![minecraftz](https://i.imgur.com/HOJLMQo.png)

6. Oh no a blank screen! 
![minecraft blank screen](https://i.imgur.com/wJjxSw8.png)

7. We need to update some video settings. At the bottom right hand corner of the screen select the `vnc` icon
![vnc icon](https://i.imgur.com/bv0pBSs.png)

8. Select the hamburger menu at the top right and then options
![hamburger menu](https://i.imgur.com/CaXhILL.png)

9. Select `troubleshooting` and then check the box that says `enable direct capture mode` and then apply.
![capture mode](https://i.imgur.com/9VAvCtO.png)

10. Ta-Da! Minecraft. Go ahead and click `start game`

## Lesson 3 - Lets make a basic temperature monitor

Note: Adapted from [this project on raspberrypi.org](https://projects.raspberrypi.org/en/projects/temperature-log)

1. If you haven't already log into your raspberry pi as in steps 23-25 in Lesson 1.

2. Select the application button at the far bottom left then system tools -> lxterminal
![loonix terminal picture](https://i.imgur.com/2oNqpHz.png)

3. Type in `sudo apt-get update && sudo apt-get -y dist-upgrade && sudo apt-get -y install raspberrypi-ui-mods` and press enter.

4. This will take some time as we upgrade the Raspberry Pi to the full desktop version. A box will come up telling you about desktop options changing, go ahead and select `ok`.

5. type in `sudo shutdown -r now` and press enter.

6. When the computer comes up from shutdown click on the terminal icon at the top left.
![new terminal icon](https://i.imgur.com/xOKnXFN.png)

7. type in `sudo apt-get -y install rp-prefapps`

8. Click on the Raspberry logo at the top left then preferences recommended software.

9. Select Programming and then `Mu` and click OK
![mu selected](https://i.imgur.com/E9f65F0.png)

10. Open a terminal window and type in `sudo apt-get -y install python3-matplotlib` and press enter.

11. type in `sudo apt-get -y install python3-pip` and press enter

12. type in `pip3 install gpiozero` and press enter

13. type in `pip3 install rpi.gpio` and press enter

14. Once it has finished installing go to the raspberry icon -> programming -> mu
![mu2](https://i.imgur.com/KcU4HgS.png)

15. Select Python3 as the default mode.

16. You can use the GPIO Zero module to find the CPU temperature. First you’ll need to import the CPUTemperature class:
```
from gpiozero import CPUTemperature
```

17. Then you can create a cpu object:
```
cpu = CPUTemperature()
```
18. Click `save` and call the file `temp`.
19. Click `run`
20.  At the prompt that comes up type in `cpu.temperature`. This is the CPU's tempature in celsius. Do a quick google search of the tempature to see what it is in Fahrenheit.
![mu temp run](https://i.imgur.com/6onbxmT.png)


