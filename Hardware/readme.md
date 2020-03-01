# Overview

This semester we're going to use [Raspberry Pis](https://www.raspberrypi.org/) to do a number of projects this semester using the Raspberry Pi's Camera, Python machine learning for image classification, and the sensehat module.

Many of the lessons are based off material found from the [raspberry pi projects](https://projects.raspberrypi.org/en/projects/) and licensed under a [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) license.


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

## Lecture - Machine Learning

1. How does your brain learn?
2. What is a nueral network.
3. Training.

A good primer on the subject can be found on [Ars Technica](https://arstechnica.com/science/2019/12/how-neural-networks-work-and-why-theyve-become-a-big-business/)

## Lesson 6 - Image Recognition
In this lesson we're going to setup our Raspberry Pi to perform basic machine learning recognition using [Tensor Flow](https://www.tensorflow.org/) an open source machine learning library originally made by Google.

1. Log onto your Raspberry Pi using Real VNC. If you don't see RealVNC on your laptop you can [download it here](https://www.realvnc.com/en/connect/download/viewer/).

2. Click on the terminal icon (top left of the screen).
![terminal icon](https://i.imgur.com/wiFSDEl.png)

3. We need to first update our packages and install some necessary software. Copy & paste the following command in: `sudo apt-get update && sudo apt install -y libatlas-base-dev && pip3 install --user tensorflow` and press enter.

4.  Lets start up Mu, our Python code editor. Go to the Raspberry Icon at the top left, then select Programming and Mu.
![mu icon](https://i.imgur.com/EnfdORv.png)

5. If Prompted, select `Python 3` and click OK.

6. Lets make sure Tensorflow - the machine learning library we're using - is working correctly. Paste the following code into your Mu window. Save the file and give it a name of `hellotensorflow`

```
import tensorflow as tf
hello = tf.constant('Hello, Girls Code Lincoln!')
sess = tf.compat.v1.Session()
print(sess.run(hello))
```

7. Click `Run` in the MU window. There will be a warning you can safely ignore and it should print the `Hello, Girls Code Lincoln!` in the window which means our tensorflow library was successfully installed.
![hello success](https://i.imgur.com/sZ2g1Sg.png)

8. Now we need to install the Image Classifier. Click on the Terminal Icon again.
![terminal icon](https://i.imgur.com/wiFSDEl.png)

9. Copy & paste in (use the right click on the mouse!) this command which will install our program `pip3 install https://dl.google.com/coral/python/tflite_runtime-2.1.0.post1-cp37-cp37m-linux_armv7l.whl`

10. Paste the following into the terminal window once step 9 finishes.  `git clone https://github.com/tensorflow/examples --depth 1` and press enter. This downloads some example code for us using Tensorflow.

11. Copy & paste the following to get to the image classification tutorial: `cd examples/lite/examples/image_classification/raspberry_pi`

12. This command downloads the pre-trained neural network to our Raspberry PI. `bash download.sh /tmp` 

13. To make sure you can see the output click on the VNC icon at the top right of the screen
![vnc](https://i.imgur.com/pEFV0zS.png)

14. Click the hamburger menu and select `Options`.
![options](https://i.imgur.com/5wWIekp.png)

15. Select `Enable Direct Capture Mode` and click `OK`
![direct capture mode](https://i.imgur.com/sM2O3uj.png)

16. GO back to your terminal window and copy and paste the following script & press enter.
```
python3 classify_picamera.py \
  --model /tmp/mobilenet_v1_1.0_224_quant.tflite \
  --labels /tmp/labels_mobilenet_quant_v1_224.txt
  ```

17. Point your Camera at various objects. The Script will display 2 things at the very top. The object it is guessing with a confidence interval & the time it took to make the guess. In the screenshot below the neural net is guessing this is a desk with an 11% confidence level and it took 308ms to complete.
![first guess](https://i.imgur.com/wt53Jcw.png)

18. In this example I added my dog to the mix. It classified it as a Chihuahua with a 39% confidence level and it took the model 305ms to do so.
![bertiebotts](https://i.imgur.com/b5WqFr7.png)

19. Try pointing the camera at various objects in the room and see how well it does at classifying the objects. When you're done hold down `ctrl c` that is the `ctrl` and the `c` key at the same time to quit the python script.

## Lesson 7 - Image Recognition with saving!
In this lesson we'll modify our Python script to save a copy of every image it classifies as well as modifying exactly what it's capturing and how it is previewing the image to us. 

Note: We'll be using the Python programming language which is _space sensitive_. Be careful when modifying the scripts you don't remove or add additional spaces!

1. Log onto your raspberry by with Real Vnc. If it isnt installed already you can [download it here](https://www.realvnc.com/en/connect/download/viewer/)

2. Open the terminal window by clicking on the terminal icon
![terminal icon](https://i.imgur.com/wiFSDEl.png)

3. Type in `mkdir models` - this creates a models directory for us to use to download our models to. Then type in `mkdir ~/Desktop/gcl` this creates a `gcl` folder on our desktop we'll use later on in the lesson.

4. Type or copy and paste in `bash examples/lite/examples/image_classification/raspberry_pi/download.sh ~/models`. This command executes the `download.sh` script which downloads the prebuilt training models to the directory `models` in your pi's home directory.

5. We're going to create a copy of the script we used in Lesson 6 that we can modify ourselves. Type in the following command to copy that script to your local directory `cp examples/lite/examples/image_classification/raspberry_pi/classify_picamera.py ~`

6. Verify your classification program is setup right by running this command which will execute the camera and classify images like we did in lesson 6. HIt `ctrl + c` to stop once it runs:
```
python3 classify_picamera.py \
  --model ~/models/mobilenet_v1_1.0_224_quant.tflite \
  --labels ~/models/labels_mobilenet_quant_v1_224.txt
```

7. Open up Mu by clicking on the raspberry icon then going to programming and then mu.

8. Select Python 3 if prompted for programing mode.

9. Click Load at the top and then on the left hand side click `pi`. Scroll down and select `classify-picamera.py` and click `open`.

10. A camera has 2 primary ways of identifying its resolution usually written as the number of pixels it can capture in width and height. A pixel is the smallest unit a camera can display or capture. It is typically a value expressed a mix of red, green, blue, black, and white as well as brightness. When we say 640 x 480 resolution that means an image that is is 640 pixels wide and 480 pixels high.

 This is also sometimes expressed as megapixels - for instance an iPhone 11 is able to capture a 12 megapixel image (4290 pixels wide by 2800 pixels tall). You multiple (4200 x 2800) = 12 million. The human eye is able to capture somewhere around 576 million megapixels. Our raspberry PI maxes out at 5 megapixel. Keep these numbers in mind when we modify the values below.


11. Scroll down to Line 75. Lets modifying our preview window to not make it full screen on our Raspberry Pi. Modify the line to read `camera.start_preview(fullscreen=False, window=(100,100,640,480))`. This will start the preview with a window that is set 100 pixels off the top of the screen, 100 pixels to the left of the screen 640 pixels tall and 480 pixels wide. Save the file and then copy and paste this to run the program. Note the window size is much smaller. Hit `ctrl + c` to stop it.
```
python3 classify_picamera.py \
  --model ~/models/mobilenet_v1_1.0_224_quant.tflite \
  --labels ~/models/labels_mobilenet_quant_v1_224.txt
```

12. Now lets see what happens when we modify the resolution that our Camera is capturing with. A higher resolution might lead to better results from our image classification program. Modify line 74 resolution to be `(1024,768)` and set the `framerate` to `15`.  Save the script. Run our program again and scan common objects. Is it better at classifying? As before, copy and paste (or hit the up arrow in the terminal window) the following code and hit `ctrl + c` to stop the camera.
```
python3 classify_picamera.py \
  --model ~/models/mobilenet_v1_1.0_224_quant.tflite \
  --labels ~/models/labels_mobilenet_quant_v1_224.txt
  ```

13. Lets turn our raspberry pi camera up to its maximum level. Modify line 74 again to set the resolution to `(2592, 1944)` and the framerate to `5`. On line 75 lets modify the preview window to be like this `window=(100,100,1024,768)`. Keep in mind with the `framerate` set to `10` you will need to let the camera point at an object for a bit longer for it to categorize the object. Save the script. As before, copy and paste (or hit the up arrow in the terminal window) the following code and hit `ctrl + c` to stop the camera.

```
python3 classify_picamera.py \
  --model ~/models/mobilenet_v1_1.0_224_quant.tflite \
  --labels ~/models/labels_mobilenet_quant_v1_224.txt
```

14. We're going to now modify to save every unique picture that we capture to a special folder. Add a new line below 90. We are going to use the [capture](https://picamera.readthedocs.io/en/release-1.10/api_camera.html#picamera.camera.PiCamera.capture) methord to save a picture and give it the label of what it classifed.
`camera.capture('/home/pi/Desktop/gcl/captured-%s.jpeg' % labels[label_id])`. Save the script. As before, copy and paste (or hit the up arrow in the terminal window) the following code and hit `ctrl + c` to stop the camera. You can let the camera run for a bit, pointing at other objects.

```
python3 classify_picamera.py \
  --model ~/models/mobilenet_v1_1.0_224_quant.tflite \
  --labels ~/models/labels_mobilenet_quant_v1_224.txt
```

15. Click the folder icon. When it opens select Desktop and then gcl folder. Inside this folder you can see your pictures, one for each of the items your classified.
![folder icon](https://i.imgur.com/T6bC2Is.png)


## Lesson 8 - Object Detection
Object detection is the ability to detect multiple things inside an image, not just the 'main' image classification as we did before. Image detection is useful in the context of self driving cars for example to detect a car versus a bike versus a street sign. In this lesson we're going to use a neural network and our raspberry pi to setup a simply image detection program.

Note: We'll be using the Python programming language which is _space sensitive_. Be careful when modifying the scripts you don't remove or add additional spaces!

1. Log onto your raspberry by with Real Vnc. If it isnt installed already you can [download it here](https://www.realvnc.com/en/connect/download/viewer/)

2. Open the terminal window by clicking on the terminal icon
![terminal icon](https://i.imgur.com/wiFSDEl.png)

3. Type or copy and paste in `bash examples/lite/examples/object_detection/raspberry_pi/download.sh ~/models`. This command executes the `download.sh` script which downloads the prebuilt training models to the directory `models` in your pi's home directory.

4. We're going to create a copy of the example script so we can modify it ourselves, like we did in Lesson 7.  Type in the following command to copy that script to your local directory `cp examples/lite/examples/object_detection/raspberry_pi/*.py ~`

5. Now let's run the object classification program as is. Copy & paste the following into the terminal. Move the cameraaround and note how it's classifying various objects. Hit `ctrl + c` to stop the program.
```
python3 detect_picamera.py   --model ~/models/detect.tflite   --labels ~/models/coco_labels.txt
```

6. Open up Mu by clicking on the raspberry icon then going to programming and then mu.

7. Select Python 3 if prompted for programing mode.

8. Click Load at the top and then on the left hand side click `pi`. Scroll down and select `detect_picamera.py` and click `open`.

9. Scroll down to line 35 and lets modify the `CAMERA_WIDTH` AND `CAMERA_HEIGHT` variables and see if the higher resolution helps the raspberry PI detect the objects better. Set `CAMERA_WIDTH` equal to `1024` and `CAMERA_HEIGHT` TO `768`. Scroll down to line 128 and set the `framerate` to `15`. Save the script.

 As before, you can type the following command in to run or hit up arrow in your terminal and then enter. Press `ctrl + c` to quit. Is the camera better at detecting images with the higher resolution?

```
python3 detect_picamera.py   --model ~/models/detect.tflite   --labels ~/models/coco_labels.txt
```

10. Unfortunately our raspberry PIs can't run at their maxium camera resolution - they'll run out of memory! Set `CAMERA_WIDTH` equal to `1920` and `CAMERA_HEIGHT` TO `1280`. Scroll down to line 128 and set the `framerate` to `5`.  As before, you can type the following command in to run or hit up arrow in your terminal and then enter. Press `ctrl + c` to quit. 

```
python3 detect_picamera.py   --model ~/models/detect.tflite   --labels ~/models/coco_labels.txt
```

11. We should capture some images and examples of its classification. Add a new line right after line 132. This line shoudl have `lastResults = 0` in it. we're declaring the variable `lastResults` and setting its initial value to `0`. Pay attention to spacing! Python is a case sensitive language.
![example](https://i.imgur.com/falen0y.png)

12. Add a new line after line 146. We're going to add an if statement that says if the length of the results is different than the last time the classification ran save the picture to our `gcl` folder. The 2 lines of code to do this are below:
```
        if len(results) != lastResults:
            camera.capture('/home/pi/Desktop/gcl/detection-%s.jpeg' % len(results))
```
![examplex2](https://i.imgur.com/pPwm3m3.png)

12. Lets run our program. Point the camera at different objects to capture some results. As before, you can type the following command in to run or hit up arrow in your terminal and then enter. Press `ctrl + c` to quit. 

```
python3 detect_picamera.py   --model ~/models/detect.tflite   --labels ~/models/coco_labels.txt
```

13. Click the folder icon. When it opens select Desktop and then gcl folder. Inside this folder you can see your pictures, one for each of the items your classified.
![folder icon](https://i.imgur.com/T6bC2Is.png)

### Lesson 9 - SenseHat Fun With Pixels

In this lesson we're going to install the Raspberry PI's [Sensehat](https://www.raspberrypi.org/products/sense-hat/) module. This module was built for the [Astro Pi](https://astro-pi.org/) mission to the International Space Station. It includes a number of sensors and lights we'll use throughout the rest of the semester.

1. Unpack your Sensehat. 
![unpack](https://i.imgur.com/WsQ0btS.png)
![sensehat](https://i.imgur.com/he7YMgr.png)

2. Remove the upper portion of your Raspberry PI's case. 

3. Push the Sensehat carefully onto the pins on the Raspberry Pi 
![attached sensehat](https://i.imgur.com/b2JE9kr.png)

4. Start up your Raspberry Pi by plugging in the power.

5. Log onto your raspberry by with Real Vnc. If it isn't installed already you can [download it here](https://www.realvnc.com/en/connect/download/viewer/)

6. Open the terminal window by clicking on the terminal icon
![terminal icon](https://i.imgur.com/wiFSDEl.png)

7. Type in or copy & paste the following `sudo apt-get update && sudo apt-get install -y sense-hat` and press enter.

8. Once it has finished installing you can close the terminal window.

9. Select Programming and then `Mu` and click OK
![mu selected](https://i.imgur.com/E9f65F0.png)

10. Type or paste the following text. Click save and save it as `sensehat.py`. once saved click Run.

```
from sense_hat import SenseHat
sense = SenseHat()
sense.show_message("Hello Girls Code Lincoln!")
```

11. You should see the message scroll across the LED screen. Change the text in between the quotes in the `show_message` method to display different messages.

12. Let's alter the color and scroll speed by adding some additional parameters to the `show_message` method.  We can change the color as well by passing in special values representing Red, Green, & Blue. Stop the program running and alter the code above to add the `red` variable with the numbers `(255,0,0)` which represent the color red.

```
from sense_hat import SenseHat
sense = SenseHat()
red = (255,0,0)
sense.show_message("Hello Girls Code Lincoln!", text_colour=red)
```

13. There are more colors available - you can use [this color picker](https://www.w3schools.com/colors/colors_rgb.asp) to get the values to use for `red`, `green`, and `blue` and use in the above code to set different color values.

14. We can also change the `back_color` of the LED as well by adding in a new parameter to `show_message` called `back_color`. Stop the program above and update it as show below. Click run when finished. 

```
from sense_hat import SenseHat
sense = SenseHat()
red = (255,0,0)
white = (255,255,255)
sense.show_message("Hello Girls Code Lincoln!", text_colour=red, back_colour=white)
```

15. Lets try changing the colors. As you have seen in the steps above the colors are represented as a `list` that loosk like `(255,255,0)`. On the Sensehat each of three numbers are used to represent red, green, & blue. Each of these color values is assigned a value between 0 and 255. By mixing and matching the values we can have different colors. For instance, to display nothing but Yellow copy & paste the following code below and click Run.

```
from sense_hat import SenseHat

sense = SenseHat()

red = 255
green = 255
blue = 0

sense.clear((red, green, blue))
```

16.  We can also directly control the LED pixels on the Sensehat as well. Each sensehat pixel is numbered using a x,y axis from the top left starting at 0. There are `8` pixels on the sensehat in each direction. Enter the following code to turn specific pixels different colors and click run.

```
from sense_hat import SenseHat
sense = SenseHat()
red = (255,0,0)
green = (0,255,0)
blue = (0,0,255)
white = (255,255,255)

sense.set_pixel(0, 0, red)
sense.set_pixel(0, 7, green)
sense.set_pixel(7, 0, blue)
sense.set_pixel(4, 4, white)

```

17. Try changing the first two parameters of `set_pixel` to move the LED that you light up around. Remember, a valid value is between `0` and `7` as the Sensehat is an 8 by 8 grid and the numbering system starts with `0`.

18. We can also set multiple pixels on the sensehat directly using the `set_pixels` method. Stop the program running above. Copy & paste the code below and click run. It should disply a question mark on the sensehat.

```
from sense_hat import SenseHat
sense = SenseHat()
X = [255, 0, 0]  # Red - feel free to change to your favorite color 
O = [255, 255, 255]  # White - feel free to change the color!

question_mark = [
O, O, O, X, X, O, O, O,
O, O, X, O, O, X, O, O,
O, O, O, O, O, X, O, O,
O, O, O, O, X, O, O, O,
O, O, O, X, O, O, O, O,
O, O, O, X, O, O, O, O,
O, O, O, O, O, O, O, O,
O, O, O, X, O, O, O, O
]
sense.set_pixels(question_mark)
```

19. We can also flip the orientation of the LED lights by using `set_rotation`. Lets turn our question_mark upside down:

```
from sense_hat import SenseHat
sense = SenseHat()
X = [255, 0, 0]  # Red - feel free to change to your favorite color 
O = [255, 255, 255]  # White - feel free to change the color!

question_mark = [
O, O, O, X, X, O, O, O,
O, O, X, O, O, X, O, O,
O, O, O, O, O, X, O, O,
O, O, O, O, X, O, O, O,
O, O, O, X, O, O, O, O,
O, O, O, X, O, O, O, O,
O, O, O, O, O, O, O, O,
O, O, O, X, O, O, O, O
] 
sense.set_pixels(question_mark)
sense.set_rotation(180)
```

### Lesson 10 - Sensehat Countdown Timer

We're going to modify the LED to display a countdown timer and learn a little bit about Python loops in the process.

1. Log onto your raspberry by with Real Vnc. If it isnt installed already you can [download it here](https://www.realvnc.com/en/connect/download/viewer/)

2.  Select Programming and then `Mu` and click OK
![mu selected](https://i.imgur.com/E9f65F0.png)

3. Add the following code to countdown from 10 to 0 into Mu and click run.

```
from sense_hat import SenseHat
sense = SenseHat()
for i in range(1,10):
  sense.show_letter(str(i))
  sleep(1)
```

4. The `for i in range(1,10)` is a `for` loop in Python. Like in other languages it means for each value of the range - 1 to 10 in this case - execute the code below it one time and use the variable `i` to keep track of which value in the range we're currently executing.

5. Change the color of the countdown to be your favorite color and run the program again.

```
import time
from sense_hat import SenseHat
sense = SenseHat()
red = (255,0,0)
for i in range(0,7):
  sense.show_letter(str(i), text_colour=red)
  time.sleep(1)
```

6. Update the countdown time to go from 60 to 0 and click run.

7. The LED has a total of 64 pixels. Lets turn each of them on as we go through our loop. Copy & paste the following code & click run. 

```
import time
from sense_hat import SenseHat
sense = SenseHat()
blue = (0,0,255)
for i in range(1,10):
  sense.set_pixel(i, i, blue)
  time.sleep(1)
```


### Lesson 11 - SenseHat Using the Sensors

You sensehat comes with a number of built in sensors. Temperature, pressure,humidity, orientation, a magnemetor and accelermetor. In this lesson we're going to learn about each of these sensors and what they do.

1. Log onto your raspberry by with Real Vnc. If it isnt installed already you can [download it here](https://www.realvnc.com/en/connect/download/viewer/)

2.  Select Programming and then `Mu` and click OK
![mu selected](https://i.imgur.com/E9f65F0.png)

3. First lets measure the ambient air pressure. Copy & paste the following code & click run. Pressure lets us easily detect changing weather conditions. 
```
from sense_hat import SenseHat

sense = SenseHat()
sense.clear()

pressure = sense.get_pressure()
print(pressure)
```

4. Now lets detect the temperature. Erase what you had entered in step 3. Copy & paste the following code and click run. This will tell us the current temperature in Celsius. 

```
  from sense_hat import SenseHat

  sense = SenseHat()
  sense.clear()

  temp = sense.get_temperature()
  print(temp)
```

5. Your PI can also sense the humidity. Erase step 4 and we can add this code to directly sense the current humidity of the environment.

```
from sense_hat import SenseHat

sense = SenseHat()
sense.clear()

humidity = sense.get_humidity()
print(humidity)
```

6. Lets out the temperature, pressure, and humidity to the display using what we learned in lesson 9. Modify the program to ouput the results using whatever your favorite color is. (????)

```
  from sense_hat import SenseHat

  sense = SenseHat()
  sense.clear()
  temp = round(sense.get_temperature(),1)
  humidity = round(sense.get_humidity(),1)
  pressure = round(sense.get_pressure(),1)

  sense.show_message("Temp: %s Humidity: %s Pressure: %s " %(str(temp),str(humidity),str(pressure)))

```

7. We can also set alerts for if the temperature exceeds a certain value. By adding a conditional we can change the color if the temperature or pressure exceeds a certain limit. Add the following line (????) of code to change the color to your preference. In this code we'll change it so as long as the temperature is between 18 and 26 C the temperature is displayed in green on the screen.

```
from sense_hat import SenseHat
sense = SenseHat()

# Define the colours red and green
red = (255, 0, 0)
green = (0, 255, 0)

while True:

  # Take readings from all three sensors
  t = sense.get_temperature()
  p = sense.get_pressure()
  h = sense.get_humidity()

  # Round the values to one decimal place
  t = round(t, 1)
  p = round(p, 1)
  h = round(h, 1)
  
  # Create the message
  message = "Temperature: " + str(t) + " Pressure: " + str(p) + " Humidity: " + str(h)
  
  if t > 18 and t < 26:
    bg = green
  else:
    bg = red
  
  # Display the scrolling message
  sense.show_message(message, scroll_speed=0.05, back_colour=bg)

```


### Lesson 12 Sensehat movement and acceleration

Your senshat has a number of sensors - like your phone - to detect movement. In this lesson we'll learn how the gyroscope, accelerometer, and magnetometer help us detect these changes.

1. Log onto your raspberry by with Real Vnc. If it isnt installed already you can [download it here](https://www.realvnc.com/en/connect/download/viewer/)

2.  Select Programming and then `Mu` and click OK
![mu selected](https://i.imgur.com/E9f65F0.png)

3. Your Sensehat can detect three types of motion - pitch, roll, and yaw. A simple explanation for these forces are:
  * Pitch - Imagine driving up a steep hill.
  * Roll - imagine rolling down a hill like a log.
  * Yaw - Imagine steering a car.

4. Lets detect the pitch, roll, and yaw of your raspberry pi. Copy & paste the following code into Mu and click run. (????)

```
from sense_hat import SenseHat
sense = SenseHat()
sense.clear()

o = sense.get_orientation()
pitch = o["pitch"]
roll = o["roll"]
yaw = o["yaw"]
print("pitch {0} roll {1} yaw {2}".format(pitch, roll, yaw))
```

5. While the program is still running try changing the direction of your raspberry pi and moving it around. Note how the values of pitch, roll, and yaw change as you move your Pi.

6. Your Pi is able to measure the acceleration in any axis as well. You can think of acceleration as the force you feel when a car starts moving forward or on a roller coaster as you plummet down. The Pi measures acceleration in terms of `G` where `1G` equals the acceleration due ot gravity at sea level - 9.8 m/s^2 or roughly 35 mph (???). We can detect the current acceleration by using the `get_accelerometer_raw` value. Copy & paste the following code in to Mu and click run. Rotate your raspberry PI and note how the value changes. 

```
from sense_hat import SenseHat

sense = SenseHat()

while True:
	acceleration = sense.get_accelerometer_raw()
	x = acceleration['x']
	y = acceleration['y']
	z = acceleration['z']

	x=round(x, 0)
	y=round(y, 0)
	z=round(z, 0)

	print("x={0}, y={1}, z={2}".format(x, y, z))
```

7. Similar to a cell phone we can use the sensor to detect the orientation of the raspberry pi and flip the screen. Stop the code from the above example, paste the code below and rotate the pi around. Note how the value on the screen changes.

```
from sense_hat import SenseHat

sense = SenseHat()

# Display the letter J
sense.show_letter("J")

while True:
	acceleration = sense.get_accelerometer_raw()
	x = acceleration['x']
	y = acceleration['y']
	z = acceleration['z']

	x=round(x, 0)
	y=round(y, 0)
	z=round(z, 0)
	
	print("x={0}, y={1}, z={2}".format(x, y, z))

  # Update the rotation of the display depending on which way up the Sense HAT is
	if x  == -1:
	  sense.set_rotation(180)
	elif y == 1:
	  sense.set_rotation(90)
	elif y == -1:
	  sense.set_rotation(270)
	else:
	  sense.set_rotation(0)
```

8. It's difficult to get a high value while slowly rotating the board but what if we shake the board? Lets make a program that outputs the value of the accelerometer onto the LED screen and changes the color if it exceeds `1G`. Erase the code from the previous examples and copy & paste the code below and click run. Shake your raspberry pi and note when it changes colors.

```
from sense_hat import SenseHat

sense = SenseHat()

red = (255, 0, 0)

while True:
    acceleration = sense.get_accelerometer_raw()
    x = acceleration['x']
	y = acceleration['y']
	z = acceleration['z']

    x = abs(x)
    y = abs(y)
    z = abs(z)

    if x > 1 or y > 1 or z > 1:
        sense.show_letter("!", red)
    else:
        sense.clear()
```

8. Lets have it print something better than `!` on the pixel screen. Alter the code from step 7 to display `Shake it off` instead of `!` when the acceleration exceeds 1G and test it out.

9. We can also have the Sensehat output the current acceleration values to the LED screen. Use the code below to display the roll, pitch, and yaw to the LED screen and change the colors to your favorite.

```
from sense_hat import SenseHat

sense = SenseHat()

red = (255, 0, 0)

while True:
    acceleration = sense.get_accelerometer_raw()
    x = acceleration['x']
	  y = acceleration['y']
	  z = acceleration['z']

    x = abs(x)
    y = abs(y)
    z = abs(z)

    if x > 1 or y > 1 or z > 1:
        sense.show_message("X: %s, Y: %s, Z: %s" % (str(x),str(y),str(z)))
    else:
        sense.clear()
```

10. Hold the raspberry pi and get _only_ the `yaw` to change. Do the same for `roll` and `pitch`.