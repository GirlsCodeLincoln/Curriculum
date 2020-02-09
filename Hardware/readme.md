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

5. Talk to the teacher to get a monitor so we can get the IP address of your Raspberry PI.

6. Plug in the power supply. Green/Red lights should come on 
![raspberry powered on](https://i.imgur.com/fvWyjcA.jpg)

7. Open up your laptop, and open Putty. If putty isnt installed on your computer you can [download it here(https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html). Fill in the IP Address from step 6 and click `open`![putty window](https://i.imgur.com/p5JEHTk.png)

8. Login to the machine with the following credentials:
```
username: pi
password: raspberry
```

9. At the command line type in `sudo raspi-config`

10. Select `change user password` and hit enter when prompted.

11. type in `girlsrule` in password and confirm password and then `ok` when the success box comes up.

12. Scroll down and select `finish`.

13. At the command prompt type `sudo apt-get update`

14. at the command prompt type `sudo apt-get install lightdm -y`

15. Type `sudo raspi-config`.  Use the arrow keys to select `interfacing options` and press `enter`

13. Select `vnc` and press `enter` and select `yes`. When prompted type in `y`.

14. Once it has finished installing, select `boot options`.

15. Select `Desktop/CLI` and then `desktop autologin`.

16. Go back to the main screen and select `<finish>` when prompted to reboot select `<no>`

17. Type in `sudo apt-get install lxsession -y` 

18. Once it has finished type in `sudo shutdown -r now` 

19. On your laptop find the program called `vnc viewer` - it'll be under a folder called `real vnc` in the start menu.

20. Enter the IP address from step 6.

21. A box will come up with a warning, select continue.

22. If prompted enter the username/password below and select `remember password`.
```
username: pi
password: girlsrule
```

23. Congratulations! You are now logged into your Raspberry PI!

## Lecture 2 - What is apt-get? What's Raspbian?

## Lesson 2 - Obligatory Minecraft Installation

1. If you havent already, log into your Raspberry PI using RealVNC as detailed in steps 19-21 in Lesson 1.

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

1. If you haven't already log into your raspberry pi as in steps 19-21 in Lesson 1.

2. Select the application button at the far bottom left then system tools -> lxterminal
![loonix terminal picture](https://i.imgur.com/2oNqpHz.png)

3. Type in (or copy and paste) `sudo apt-get update && sudo apt-get -y dist-upgrade && sudo apt-get -y install raspberrypi-ui-mods` and press enter.

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

## Lesson 4 - Music time!
In this exercise, we're going to setup our raspberry PI to play music as well as handle some basic
programming tasks.

1. Log in to your raspberry PI using RealVNC. See steps 19-21 in Lesson 1.

2. Click on the Raspberry icon at the top left then go to Accessories -> Terminal.
![click here!](https://i.imgur.com/q89wflg.png)

3. Type in `sudo apt-get update`. This ensures we have the latest packages available.

4. Type in `sudo apt-get install -y apt-transport-https`. This allows the package manager to download packages over https which we need for the next step.

5. We now need to add the secure key used to digitally sign the packages to our allowed list of keys. Paste the following command in the terminal window. `curl https://downloads.plex.tv/plex-keys/PlexSign.key | sudo apt-key add -`

6. Now we can add the Plex server to our allowed list of package sources. Copy & Paste this into the terminal window.
`echo deb https://downloads.plex.tv/repo/deb public main | sudo tee /etc/apt/sources.list.d/plexmediaserver.list`

7. Type in `sudo apt-get update` to again update our apt-get with the list of available package sources.

8. Now (finally) we can install the plex media server and Chromium - the basic chrome browser. Type in `sudo apt-get install -y plexmediaserver && sudo apt-get install -y chromium`.

9. Lets start our media server using the `systemctl` - or system control - utility by typing in `sudo systemctl start plexmediaserver`

10. On your raspberry pi go to the raspberry icon then internet then chromium web browser.

11. Open up [last.fms free download page](https://www.last.fm/music/+free-music-downloads?page=1)

12. Right click on a random song and select `save link as`

12. Select music on the left hand side and then click save at the bottom right.

13. Open a new chromium tab on the Raspberry and go to http://127.0.0.1:32400/web 

14. On the screen that comes up here at the very bottom right click `whats this`
![stupid sign in](https://i.imgur.com/T3GQ4my.png)

15. On the next screen click `skip and accept limited functionality.`

16. Click `Got It` and then close out of the screen offering stuff.

17. Where it says `give me a friendly name` call your PI `GCL - {YOURNAME}` replacing `{YOURNAME}` with your real first name:
![plex setup 2](https://i.imgur.com/qZx2jab.png)

18. Click `Add Library` and then `Music`. Under name leave it select as `Music` and click Next.

19. Click `browse for media folder`.

20. IN the box type in `/home/pi/Music` and then `Add` and `Save Changes`
![plex add media folder](https://i.imgur.com/6CGaAtW.png)

21. You can close out of this window. On your phone open up the app store and install the `plex` media player.

22. Open up the plex app and chose `skip`. Tap `click and accept limited functionality` and then `skip` again. Click `let's go.`

23. Tap the hamburger menu and then tap `music`.

24. At the top you should see `GCL - YOURNAME` and the song you added above.


## Lesson 5 - Setting up our Pi Camera!
In this lesson we're going to install and do the basic setup of the Camera for our Raspberry PI.

1. Shut off your raspberry pi.

2. Unbox the camera.
![camera pic](https://i.imgur.com/rAZibJ4.jpg?1)

3. Remove the top part of your case.

4. Place the raspberry pi flat on the desk and remove the top cover - there are 4 clips along the outside edge of the case that you'll need to undo.

5. Watch the [video here](https://youtu.be/1VyE5-gv6jA?t=39) for installation of the camera.

6. On the camera port there are two notches. Gently lift up each side of the notch
![camera notches](https://i.imgur.com/llk7NAs.jpg)

7. Slide the cable into the gap. Pay attention and note the cable is inserted in the correct direction
![camera insert](https://i.imgur.com/hUkyPs8.jpg)

8. Push the cable in securely and then gently push on both notches to lock it in place.

9. See [the following video](https://youtu.be/1VyE5-gv6jA?t=35) for how to put the cse back on and secure the
camera.

10. Plug back in your raspberry pi.

11. Use VNC to connect to your computer (see steps 19-21 on lesson 1).

12. Go to the raspberry icon then preferences and raspberry pi configuration.
![raspberry pi config](https://projects-static.raspberrypi.org/projects/getting-started-with-picamera/66647ad6c4dc1f0db22f367955a8c108dce2d290/en/images/pi-configuration-menu.png)

13. If a box comes up that says "reboot required" select "yes".
![reboot required](https://i.imgur.com/jhQzG1w.png)

14. Now lets make sure the camera is working. Open up the `terminal`.
![image](https://projects-static.raspberrypi.org/projects/getting-started-with-picamera/66647ad6c4dc1f0db22f367955a8c108dce2d290/en/images/open-terminal-annotated.png)

15. In the command line paste in `raspistill -o Desktop/image.jpg` and press enter. The camera will preview for 5 seconds and then take the picture.

16. We can also record video with raspivid - `raspivid -o Desktop/video.h264  -t 20000`. The following command will record 20 seconds of video and save it to your desktop.

17. Type the following command to install VLC a free video player, some Python modules we'll need for the next section, and Mirage a image viewer. `sudo apt-get install -y vlc python-picamera python3-picamera mirage`.

18. After VLC has installed you should be able to double click on the `video.h264` icon on the desktop to play your video.

19. Go to Raspberry -> Programming -> Mu

20. Select `python3` as the mode if prompted.

21. Copy and paste the following code and click `save`. Name it `camera.py`.
```
from picamera import PiCamera
from time import sleep

camera = PiCamera()

camera.start_preview()
sleep(5)
camera.stop_preview()
```

22. Click the `run` button. You should see a 5 second preview and then the image will stop.

23. Click the `stop` button.

24. Lets fix the cameras rotation. Add a line brefore `camera.start_preview()` that sets the rotation correctly - `camera.rotation = 270` and click `run`.

25. Now lets take a picture with Python. Add the following line right after `sleep(5)` to save a picture on your desktop - `camera.capture('/home/pi/Desktop/gcl-image2.jpg')` and click `run`.

26. What if we want to take a series of pictures? Python supports loops like that below. The code below will count from 0 to 4 and take a picture after 5 seconds. Each picture will be saved on your desktop with the `%` in the file name replaced with the number in the loop. So `0`, `1`,`2`,`3`,`4`. Go ahead and replace everything after `camera.start_preview()` with the code below and click `run`.

```
for i in range(5):
    sleep(5)
    camera.capture('/home/pi/Desktop/image-gcl%s.jpg' % i)
camera.stop_preview()
```

27. You should see 5 new images on your desktop.

28. Now lets record a new video. Amend your code to look like this:
```
from picamera import PiCamera
from time import sleep
camera = PiCamera()
camera.rotation = 270

camera.start_preview()
camera.start_recording('/home/pi/Desktop/pyvideo.h264')
sleep(5)
camera.stop_recording()
camera.stop_preview()
```

29. The camera offers a number of options to change the framerate and resolution. Lets set the maximum resolution and take some pictures with the following code. Paste this in and click run.

```
from picamera import PiCamera
from time import sleep
camera = PiCamera()
camera.rotation = 270

camera.resolution = (2592, 1944)
camera.framerate = 15
camera.start_preview()
sleep(5)
camera.capture('/home/pi/Desktop/max.jpg')
camera.stop_preview()
```

30. We can also add text to our image. Try the following code below

```
from picamera import PiCamera
from time import sleep
camera = PiCamera()
camera.rotation = 270

camera.start_preview()
camera.annotate_text = "Hello Girls Code Lincoln!"
sleep(5)
camera.capture('/home/pi/Desktop/text.jpg')
camera.stop_preview()
```

31. We can change the color and size of the text as well with the following code. Note the `import PiCamera, Color` to add in the ability to set `Color` and the `annotate_text_size` to set the text size.

```
from picamera import PiCamera, Color
from time import sleep
camera = PiCamera()
camera.rotation = 270

camera.start_preview()
camera.annotate_background = Color('blue')
camera.annotate_foreground = Color('yellow')
camera.annotate_text_size = 50
camera.annotate_text = " Hello Girls Code Lincoln "

sleep(5)
camera.stop_preview()
```

32. There are a number of [camera effects](https://picamera.readthedocs.io/en/release-1.10/api_camera.html#picamera.camera.PiCamera.image_effect) we can use too with the `image_effect` option. Lets try it with `cartoon`.

```
from picamera import PiCamera
from time import sleep
camera = PiCamera()
camera.rotation = 270

camera.start_preview()
camera.image_effect = 'cartoon'
sleep(5)
camera.capture('/home/pi/Desktop/cartoon.jpg')
camera.stop_preview()
```

33. We can also try _all_ the image effects available with this loop:

```
from picamera import PiCamera
from time import sleep
camera = PiCamera()
camera.rotation = 270

camera.start_preview()
for effect in camera.IMAGE_EFFECTS:
    camera.image_effect = effect
    camera.annotate_text = "Effect: %s" % effect
    sleep(5)
camera.stop_preview()

```