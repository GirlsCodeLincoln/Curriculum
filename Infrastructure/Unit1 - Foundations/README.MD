# Unit 1 - Foundations

## Overview
In this unit we're going to build the necessary cloud infrastructure to setup our very own [Minecraft](https://www.minecraft.net/en-us/) server on the cloud. During this lesson we'll learn about the fundamentals of creating networks & virtual machines, securing those resources, and what exactly is 'the cloud'.

### Goals
At the end of this session students should be able to understand [the following CSTA standards](https://www.doe.k12.de.us/cms/lib/DE01922744/Centricity/Domain/176/CSTA%20Computer%20Science%20Standards%20Revised%202017.pdf)

1B-NI-04 - Model how information is broken down into smaller pieces, transmitted as packets through
multiple devices over networks and the Internet, and reassembled at the destination.
1B-NI-05 - Discuss real-world cybersecurity problems and how personal information can be protected
1B-IC-21 - Use public domain or creative commons media, and refrain from copying or using material
created by others without permission.
2-CS-02 - Design projects that combine hardware and software components to collect and exchange
data.
2-NI-04 - Model the role of protocols in transmitting data across networks and the Internet.
2-NI-05 - Explain how physical and digital security measures protect electronic information.
2-NI-06 - Apply multiple methods of encryption to model the secure transmission of information.
3A-CS-02 - Compare levels of abstraction and interactions between application software, system
software, and hardware layers.

### Lesson 1 - The Basic Building blocks of Cloud Infrastructure

During this Lesson we'll go over the basics of computer infrastructure - Servers & Networks. We'll explore what a cloud is and how to use it to build computing infrastructure.

### Exercise 1 - Build our Virtual Server

A [minecraft server](https://minecraft.gamepedia.com/Tutorials/Setting_up_a_server) requires just a handful of things to work correctly. The very first thing it needs is an actual server to run the software on.

1. Log onto the [AWS Console](https://aws.amazon.com/console/)
2. Select `Launch a virtual machine` with EC2
![ec2 launch](https://i.imgur.com/9aTABTm.png)
3. The first selection involves picking the image (the operating system) we use to build the machine. In this instance we can select the `Amazon Linux 2 AMI (HVM), SSD Volume Type` image. It should be the first image listed.
4. The next screen will ask us to select the _size_ of the virtual machine. In this case the default (t2.micro) is fine for our purposes. Select it and click the `Review and Launch` button.
5. A box comes up that lets us review the selection. Go ahead and click `Launch`
6. A prompt will come up asking us for the `key pair` used to connect to the machines. This key is a way of connecting securely to our machines without needing a password. Go ahead and select `create a new key pair` and enter `minecraft server` for the key pair name.
7. Click the Download Key Pair button. Save the file to your desktop.
8. Click `Launch Instance` again
9. The cloud will now start creating your server. Click the `view launch log` to watch the progress.
10. When its complete click `view instances`
11. We have our server! Now we need to connect to it and setup minecraft. Make a note of the `ipv4 public ip` listed in the view screen.
12. Click the `connect` button at the top left. Select `EC2 Instance Connect (browser-based SSH connection)` as the connection option & click `connect`.
13. You are now in a unix shell on your very own server! The first thing we do for security purposes is type `sudo yum update -y` to install critical security patches. 
14. all done! Your virtual machine is now ready for the next step.

### Lesson 2:  Computing Building Blocks

The key building block of everything we do is a computer. In this lesson we'll explore the basics behind computers (CPU, Cores, Storage, Network, & Memory) and how they influence computer performance.

### Exercise 2: Understanding your Minecraft Virtual Machine

In this exercise we'll examine the server you created in Exercise 1 to better understand its capabilities.

1. Log onto the [AWS Console](https://aws.amazon.com/console/)
2. At the top left click `services` and then `ec2`
3. On the left select instances.
4. You should see your server listed. Select in and note the `instance type` is set to `t2.micro`.
5. Open a new tab browse to the [aws T2 instance page](https://aws.amazon.com/ec2/instance-types/t2/) and find your `t2.micro`. Note how many vCPUs & how much memory is available to your server.
6. Go back to your dashboard and select `Launch Instance`
7. Select `Amazon Linux 2 AMI (HVM), SSD Volume Type`
8. Scroll through the list and notice the different options available. Notice how the primary difference between virtual machines available is the `vCPUs`, `Memory`, `Storage`, and `Network` available.
9. If you wanted to make sure your minecraft server could handle large amounts of users what virtual machine might you select from that list? Why?
9. click cancel

### Group Activity #2: Selecting a Virtual Machine

Break up into groups of 2-3 and take 5-10 minutes to answer the following questions.

1. Suzy Salesperson needs an application deployed onto the cloud. The application needs a lot of CPU resources (The recommendations say 16+ CPUs) but lists hard disk requirements as only needing 50GB of space. What Virtual Machine type would you suggest? Why?

2. Hector from accounting needs a virtual machine to host his accounting databases backup. He's not too sure on the CPU requirements but informs you that it processes a lot of data from other database servers across the network. He also needs as much disk space as you can give. Which VM type would you choose? Why?

### Lesson 3: Understanding Virtual Machines

Virtual machines underpin virtually all of computing from our cell phones to the web browser to the machines that will run our minecraft server. We'll go over the basics of what virtualization is & why it's so widely used across all of computing.

### Exercise 3: Installing the Java Virtual Machine (JVM) and Minecraft

In this exercise we'll install the JVM and finally install our minecraft server software on the JVM.

1. Log onto the [AWS Console](https://aws.amazon.com/console/)
2. At the top left click `services` and then `ec2`
3. On the left select instances.
4. Select your instance and click `connect` & select `EC2 instance connect (browser based ssh connection)`
5. type in `sudo amazon-linux-extras install java-openjdk11` and select `y` when prompted. This command installs the latest version of the java virtual machine.
6. type in `mkdir minecraft` to create a minecraft directory.
7. type in `cd minecraft`.
8. type in `wget https://launcher.mojang.com/v1/objects/3dc3d84a581f14691199cf6831b71ed1296a9fdf/server.jar` this will download the minecraft server -- the `server.jar` to your minecraft directory.
9. type in `java -Xmx1024M -Xms1024M -jar server.jar`.
10. An error message should appear letting us know that we need to accept the eula (End User License Agreement)
![End User Agreement](https://i.imgur.com/ItZyQBt.png)
11. type in `nano eula.txt` this will start the Nano text editor to edit the eula.txt file.
12. Use the arrow keys to scroll down and change the line to read `eula=true`
13. Hit Ctrl+X and then `Y` and then press enter to save your changes
14. Enter `java -Xmx1024M -Xms1024M -jar server.jar` to start your minecraft server again.
15. Your minecraft server will now begin its startup script.
![Minecraft Startup](https://i.imgur.com/vMwhb63.png)

### Lesson 4: Networking
Your minecraft server is up but how do players connect to it? In this Lesson we'll go over the basics of how networking works on the internet.

### Exercise 4: Setting up your network
1. Log onto the [AWS Console](https://aws.amazon.com/console/)
2. At the top left click `services` and then `ec2`
3. On the left select instances.
4. Make sure your machine is started. If the Instance State isn't `running` select your machine, click actions, and then start. Click Yes, Start when prompted.
5. On the left hand pane under `Network & Security` select `Security Groups`
6. Click `Create Security Group`
7. Under `Security Group Name` enter `Minecraft`, for description enter `Minecraft` and leave the `VPC` selected as the default. 
8. Under `inboud rule` select `add rule`.
9. Leave type as `Custom TCP Rule` and enter `25565` into the `Port Range`. For `Source` add `anywhere`.
10. Click `add rule` and then under `type` select `Custom UDP Rule` and enter `25565` into the `Port Range` For `Source` add `anywhere`.
11. Click `Create`
12. On the left hand side click `Instances`
13. Select your running instance and then right click on it and select `Networking -> Change Security Groups`.
14. Check the box that says `Assign Security Groups`.
15. Select `connect` and then select `EC2 instance connect (browser based ssh connection)`.
16. type in `cd /etc/init.d`
17. copy & paste the following line `sudo wget -O minecraft "http://minecraft.gamepedia.com/Tutorials/Server_startup_script/Script?action=raw"`
18. type in `sudo nano minecraft`
19. Change the `service` value to be `server.jar`
19. Change the `world` valueto be `'default'`
20. Change `username` value to be `'ec2-user'`
21. Under `MCPATH` change the path value to be `'/home/ec2-user/minecraft'`
22. Change the `BACKUPPATH` value to be `'/home/ec2-user/minecraft.backup'`
23. Change the `invocation` value to be `"java -jar $SERVICE $OPTIONS"`
24. Hit `CTRL + X` and then `enter` and `y`
25. Enter in `sudo chmod a+x /etc/init.d/minecraft`
26. type in `service minecraft start`
27. Go back to your AWS Console page. Select your instance and scroll to the bottom and select `description`.
28. Copy the IPv4 Public IP.
29. OPen a new browser tab. Enter the following URL, replacing the `{IP}` with the value you got in step 28. http://{IP}:25565 . If we did everything correctly we should get an error messaging saying ERR_INVALID_HTTP_RESPONSE
30. You can see an example of a blocked port by going to any other port on the ip - `http://{IP}:123` for example will return a can't connect error message.


#### Exercise 4A: Wordpress setup
Our minecraft server is setup but we also want a nice website so we can advertise how great our server is (as well as deploy some code to). To do that we're going to use a very popular webserver called [wordpress](https://wordpress.com/).

1. Log onto the [AWS Console](https://aws.amazon.com/console/)
2. At the top left click `services` and then `ec2` and then `instances`
3. Click `Launch Instances` and in the searchbox type in `wordpress` and select the results in the AWS Marketplace.
4. `Select` the one labelled `WordPress Certified by Bitnami and Automatic`
5. Click `continue`
6. Select the `t2.micro` type (where it says free tier eligible under type)
7. Click `Review & Launch` and then `Launch`.
8. Select `choose an existing key pair` and then select `minecraft server`
9. Click `Launch Server`
10. Wait for your server to finish starting and then at the top left click `services` and then `ec2` and then `instances`
11. You should see 2 running instances now. Your minecraft server & the running wordpress server. We can find out which is which by clicking on each and scrolling down to under `security groups` or `ami`. The wordpress server will having something in those groups saying `WordPress Certified..`. Lets give them each a name. At the top in the list of instance click into the `name` column and give the minecraft & wordpress servers a dedicated name.
12. Select your wordpress server right click and select `instance settings -> get system log`.
13. Scroll down in the log until you see the password listed like in this screen shot
![wp screenshot](https://docs.bitnami.com/images/img/platforms/aws/cm-app-credentials-3.png). It is likely towards the bottom of the log. Copy the password and click `close`
14. Note the `ipv4 public ip` listed in the column for your wordpress server. Open a new browser tab and go to `http://{IP}/wp-admin` replacing `{IP}` with the value from the `ipv4 public ip column`.
15. Type in `user` and paste in the password from step 13 into the password box and click `log in`.
16. Lets quickly change the password of our user. At the very top right of the screen where it says `howdy, user` click. 
17. Scroll down and click `generate password`. Type in our password and click `update profile`.
18. Click on `Dashboard` at hte top left and then `customize your site`.
19. Change the title or tagline and then click `publish`
20. Open a new browser tab and go to `http://{IP}` replacing `{IP}` with the value from step 14.


### Lesson 5: Monitoring
Building infrastructure and making it available is only part of our job - we also need to monitor our services to make sure we know they're always available. Learn about the basics of service monitoring.

### Exercise 5: Setup monitoring for our server
We've created our minecraft server & web server and allowed network traffic to it. Last step to running our infrastructure is setting up monitoring to notify us if our server is running into any problems.

1. Log onto the [AWS Console](https://aws.amazon.com/console/)
2. At the top left click `services` and then `ec2` and then `instances`
3. Right click on the `minecraft` instance and then `Cloud Watch Monitoring`. Select `Add/Edit Alarms`.
4. Click `Create Alarm` and then `close`
5. Check the box that says `Send a notification to...` and then click `create topic`.
6. Enter `girlscodelincoln{X}@gmail.com` in the `With these recipients` box replacing `{X}` with the
name of the account you using.
7. Where it says `Manually enter a topic name...` enter `minecraft_alert`
8. Set the alert to `Average` of `CPU Utilization` and then enter `50` percent.
9. Change to For at least `1` consecutive periods(s) of `15 minutes`.
10. Click `Create Alarm`.
11. Right click on the `minecraft` instance and then `Cloud Watch Monitoring`. Select `Add/Edit Alarms`.
12. Click `Create Alarm`
13. Check the box that says `Send a notification to...` and then enter `minecraft_alert`.
14. Under `Whenever` select `Status Check Failed (Any)`
15. For at least `5` consecutive periods of `1 minute`
16. Click `Create Alarm` and then `close`

### Lesson 6: Autoscaling
As we build these services - our minecraft and wordpress servers - and monitor what happens if we get a spike in traffic? How do we handle sudden user load effectively?

- CPU autoscaling
- Memory autoscaling
- Network scaling
- Custom

### Exercise 6: Autoscaling
1. Log onto the [AWS Console](https://aws.amazon.com/console/)
2. At the top left click `services` and then `ec2` and then `instances`
3. Right click on the `minecraft`  and select `instance settings` and then `attach to auto scaling group`.
4. Select `a new auto scaling group` and enter `minecraft` for the group name.
5. click attach
6. Click the link in the center of the confirmation box that says `minecraft` to view your auto scaling groups configuration.
7. Select `Actions` and then `Edit`.
8. Enter `2` for the `max` number of instances and select `save`.
9. Scroll down and select the `scaling policies` tab at the bottom of the screen.
10. Click `add policy`.
11. Under `name` enter `CPU Scaling` select `average cpu utilization` and then enter `90` for target value 
12. Under `instances need` enter 600.
13. Click `create`.

### Lesson 7: Cloud Building Blocks
We've done the basics of building a cloud infrastructure - we've setup a application server (minecraft) and a web server. Lets talk about the different basic building blocks of modern infrastructure and how it works.

- Databases
- Queues
- Load Balancers
- Storage
- Event Driven Services
- API Gateways
- Containers
- Virtual Machines
- Firewalls
- Cache
- Autoscaling

### Exercise 7: Cat Pictures please
Your company, Cat Corporation, has decided to launch a new product - the Cute Cat Camera. This camera will be put on your cats collar and capture continuous pictures of your cat doing cat things and uploading it to hte internet so the cats hoomans can see what the cat is doing most days (your guess is sleeping). 

You lead the infrastructure team who is responsible for building out the infrastructure to handle these tens of thousands of cat pictures that are going to be coming in to your servers at all hours of the day. The key requirements for you are:

- A website where users can view the cat pictures.
- A web service where your cat collar cameras can upload their pictures
- A database that can store all these pictures.
- The ability for the pictures to show up within 5-15 minutes on the website.
- The ability for your web servers and web services to automatically scale in case of a sudden increase in cat pictures being uploaded.
- A public API that can be used for third party partners.

Draw out what you think a good infrastructure of this would look like knowing all you now know about cloud infrastructure!
