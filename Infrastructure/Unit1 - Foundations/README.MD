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
9. type in `java -Xms1G -jar server.jar`. This command allocates 1GB of memory to our minecraft server at start and lets it grow to a maximum of 1GB.
10. An error message should appear letting us know that we need to accept the eula (End User License Agreement)
![End User Agreement](https://i.imgur.com/ItZyQBt.png)
11. type in `nano eula.txt` this will start the Nano text editor to edit the eula.txt file.
12. Use the arrow keys to scroll down and change the line to read `eula=true`
13. Hit Ctrl+X and then `Y` and then press enter to save your changes
14. Enter `java -Xms1G -jar server.jar` to start your minecraft server again.
15. Your minecraft server will now begin its startup script.
![Minecraft Startup](https://i.imgur.com/vMwhb63.png)

### Lesson 4: Networking

Your minecraft server is up but how do players connect to it? In this Lesson we'll go over the basics of how networking works on the internet.