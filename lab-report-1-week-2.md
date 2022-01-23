# Derek Ma Lab Report

Hello! This is my lab report with the topic on remote access.

## Installing VSCode

To install VSCode, or Visual Studio Code, we need to go to the VSCode website, which we can access [here](https://code.visualstudio.com/). 

The website should look something like this:

![VSCode installation](ScreenShotOne.png)

Follow the blue "Download" button on the top right and download the appropriate version that we need to install for our operating system. Once we download the installer, follow the instructions, and VSCode should be installed into our system.

## Remotely Connecting

To remotely connect, make sure we have OpenSSH installed on our system. If unsure, refer to the instructions [here.](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)

Once OpenSSH is installed, find our course-specific account for CSE15L, which can be found [here.](https://sdacs.ucsd.edu/~icc/index.php)

Once we find our login information, open up the terminal and type in this command:

`ssh cs15lwi22aug@ieng6.ucsd.edu`

Of course, the address itself will be slightly different for each user, but it should look very similar. Press enter, and if we are connecting for the first time, we will likely get a message that asks is if we are sure we want to connect to this server. Enter "yes" to continue the connection process. Then type in the password, and we should be logged in. Our screen should look something similar to this:

![RemoteConnection](ScreenShotTwo.png)

## Trying some commands

Now that our computer is connected to one of the computers in the UCSD CSE basement, we can try out some commands in our computer (the client) and it will execute those commands remotely on the computer we're connected to (the server).

Let's try these commands:

* ls - This will list all the files in the current directory (ls stands for list)

* cd [target directory] - This change the current directory to the target directory (cd stands for change directory)

* pwd - This will print the current directory that we are in (pwd stands for print working directory)

* cp [file] [target directory] - This will copy (cp) the file that we have and move it to the target directory.

Here is a screenshot of me playing around with these commands. As we can see, I copied a file from the home directory into perl5, changed the directory into perl5, listed the contents of the directory, and then printed the working directory.

![commands](ScreenShot3.png)

## Moving Files with "scp"

We can also copy files between the client and the server, but instead of using "cp" (copy), we will be using "scp" (secure copy). The difference between cp and scp is that we will need to enter a password to secure copy a file from the client to the server.

To use scp, we will need to log out of the server and go to the directory on our local machine to find the file we are looking for.

Now use the scp command in this syntax:

"scp [file name] [server address: directory]"

For my case, I have a file called "WhereAmI.java" on my local machine. I want to move it to the home directory of "cs15lwi22aug@ieng6.ucsd.edu". So, I would type this command:

![secure copy](ScreenShot4.png)

As we can see, after running the command, it prompted me for the password to login to the server. After entering the password, the file was successfully copied from my local machine onto the server.

## Setting an SSH Key

If we are using windows, follow the directions [here.](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation)

I created a pair of public and private keys using the command `ssh-keygen -t ed25519`. Following the document instructions, this created a pair of keys in a .ssh folder located on my machine. Now, I need to copy the public key from my local machine onto the server.

Login to the server using ssh, and create a new directory called .ssh by typing the command `mkdir .ssh`. Then, log out of the server.

Locate the directory of the public key that we created, and copy it into the .ssh/authorized_keys directory on the server using the "scp" command. Here is a screenshot of the scp part.

![sshkey](ss5.png)

As we can see from this screenshot, I no longer need a password to log in to the server.

## Optimizing Remote Running

For java files, we have to execute multiple commands in order to run the file. First we need to compile the file using the "javac" command, and then we would run the file itself by using the "java" command. If we are making constant changes to a java file, this may be tedious. However, since we can run multiple commands on the same line, and we have to run these 2 same commands every time in order to run the file, why not combine them both into one line?

For "WhereAmI", we could simply combine both commands into "javac WhereAmI.java; java WhereAmI". This will make running slightly easier. Of course, we would first make changes to the file on the local machine and then secure copy it to the server, but once we do that, we can log in using ssh, and then just type "javac WhereAmI.java; java WhereAmI", and run both commands at the same time. We can also use this command on our local machine to run the files on our local machine faster, too.

![orr](ss6.png)

As we can see, instead of having to type 2 commands to compile and then run the file, we only needed to type one. Small but decent improvement!