# Introduction 
One of the most important aspects in programming is to be able to work wherever you can no matter where you are. You are probably wondering how this can be done 
since this sounds like it can be really difficult however, this is really simple. The key to be able to do such thing is thorugh remote servers. They can be easily 
accessed and in this lab report I will be going over the steps on how you can connect to a remote server using an code editor called VS Code. By the end of the lab 
you should be able to remotley connect to a server using a ieng6 account thorugh VS Code.

# Installing VS Code
Before we try to connecting to a server we need to install VS Code as this will be the code editor we will be using to access the server. In my case I didn't have 
to installed VS Code as I had already installed since it was required for CSE 11 last quarter at UCSD. However, if you don't have VS Code install yet you can easily 
find it by going to this [link](https://code.visualstudio.com/). Click on the download which corresponds to your system (Windows/Mac) and follow the setps on the setup 
wizard. Once installed, open VS Code and you should see a screen similar to this:

![Image](VSCode_Screenshot.png)

*If you can see this screen then you have installed VS Code correctly*

# Gaining access to your ieng6 account
Now that you have VS Code the next step is to get access your ieng6 account as this will allow you to conect to the sever we are trying to reach. IN order to do this
you need to head to this [link](https://sdacs.ucsd.edu/~icc/index.php) in which you will look up your CSE 15L account. Once you reach this link you should see the following:

![Image](Account.png) 

On this page it will prompt you to put in your username which will be your TritonLink username and your PID number. Afterwards you should reach a screen that look like this:

![Image](id1.png)

Once you see this screen write down your username as this is the username you will be using to connect to the server and to reset your password. Now click the Global link and select the following link:

![Image](password.png)

In the username box enter the username you copied down from ealier and follow the instructions to reset your password.

# Connecting to the server
Once all the perivous steops are completed we are finally ready to connect to the server. The first step is to go to VS Code and open the terminal by going to Terminal
--> New Terminal (Ctrl or Command +) in which a new termial should appear. Once you have a termial open enter the following:\
**ssh cs15lsp23zz@ieng6.ucsd.edu**\
*The zz will be differnt for everyone make sure to use your username from earlier*

If this is your first time connecting you may see the following: 

⤇ ssh cs15lsp23zz@ieng6.ucsd.edu \
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established. \
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec. \
Are you sure you want to continue connecting (yes/no/[fingerprint])? 

In which you can type yes. It will then ask for a password which will be the new password you set up ealier. Once done you should see a screen like this:

![Image](terminal.png)

Once you reach this screen you can give yourself a pat on the back you have successfully connected to the server!

# Having fun with commands
Now that we have successfully connected to the server lets try out some new commands in the terminal to see what they do. A list of commands can be found here along:

- cd ~
- cd
- ls -lat
- ls -a
- cp /home/linux/ieng6/cs15lsp23/public/hello.txt ~/
- cat /home/linux/ieng6/cs15lsp23/public/hello.txt
  
Here is example of what we can see after running the command **ls -lat**:
  
![Image](ls-lat.png)

Congratulations you have now successfully connected to a server remotely and tried out some commands in the terminal! Thanks to this ability you are able to work 
on different servers from all over the world as long as you have a good connection and access to the server. This is a skill that can be very useful in the future as in the prgramming world you won't be able to travel all over the place instantly to fix servers so being able to connect remotely can be very useful in being able to fix servers from different places at anytime. 
