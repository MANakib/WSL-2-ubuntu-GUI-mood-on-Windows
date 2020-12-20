# WSL-2-ubuntu-GUI-mood-on-Windows
Install a graphical user interface (GUI) with Ubuntu 20.04 running within WSL 2 on a Windows 10 computer. Microsoft have announced that an RDP based GUI will be added to WSL2
-----------------------------------------------------------------
# Windows Subsystem for Linux Installation Guide for Windows 10.

Step 1 - Enable the Windows Subsystem for Linux
You must first enable the "Windows Subsystem for Linux" optional feature before installing any Linux distributions on Windows.

Open PowerShell as Administrator and run:

* dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

Step 3 - Enable Virtual Machine feature
Before installing WSL 2, you must enable the Virtual Machine Platform optional feature.

Open PowerShell as Administrator and run:

* dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

Restart your machine to complete the WSL install and update to WSL 2

Step 4 - Download the Linux kernel update package
Download the latest package:

https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi

Follow this link to next step for upgrading WSL 1 - 2 and install Ubuntu from Microsoft store.

Using " wsl -l -v " command will help you the current status of your image. 

# Step - 1

Open your terminal in my case i used my Windows Terminal which is very interactive: 

* "sudo apt update && sudo apt -y upgrade"

put your password. 

# Step - 2

install RDP:

* "sudo apt install xrdp"

# Step - 3
Now install light waight GUI here i install xfce4

* "sudo apt install -y xfce4"

here you will get a pop up menu and select "gdm3"

# Step - 4

I installed additional software 

* "sudo apt install -y xfce4-goodies"

for taking backup configuration you may use this command so that you can revart back if you have done any mistake.

* "sudo cp /etc/xrdp/xrdp.ini /etc/xrdp.ini.bac"

Here i changed the port number:

* "sudo sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini"

Here i setup the resulation with my windows & ubuntu make sure that we have a good quality.

* "sudo sed -i 's/xserverbpp=24/#xserverbpp=24\nxserverbpp=128/g' /etc/xrdp/xrdp.ini"

Now i am going to save this to as "xsession"

* "echo xfce4-session > ~/.xsession"

Now i am starting my machine to access with full remote GUI Ubuntu 

* "sudo nano /etc/xrdp/startvm.sh"

# RDP from windows 

<img width="320" alt="Windows RDP 'localhost:3390' " src="https://user-images.githubusercontent.com/10571987/102717854-1de43e80-430f-11eb-8e7c-84f6b540f94f.png">

Enter your user name & password
# Boom
 Your GUI Ubuntu on windows WSL-2 is ready to use.

![Ubuntu running on windows](https://user-images.githubusercontent.com/10571987/102718124-b0d1a880-4310-11eb-9035-bf67b67d9653.jpeg)
