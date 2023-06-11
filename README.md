# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system

## OUTPUT:
![eht 5 1](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/be68d26d-5b46-47e9-bf87-d3256354691c)

Invoke msfconsole:

## OUTPUT:
![eht 5 2](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/7b9e107b-13c1-452b-84e2-f712073ad9ae)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
![eht 5 3](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/0e053965-1f31-4373-baa5-4da92f6ab0c5)


Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:
![eht 5 4](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/9a2d5948-b31c-4465-99cf-c6bb878abb96)

use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24

## OUTPUT:
![eht 5 5](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/ffe7d85f-9369-4452-9112-8456f06900a9)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l

## OUTPUT:
![eht 5 6](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/b59f404b-9a9f-4361-94e8-655dea21e29c)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

## OUTPUT:
![eht 5 7](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/bba2a019-5f87-4491-8d7d-0c59dab13939)


The info command provides information regarding a module or platform,

## OUTPUT:
![eht 5 8](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/07cf6612-08f7-4473-bf70-d0f1f054cd3d)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
##MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
![eht 5 9](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/8d8c6471-d5d9-45dc-9223-c176945b3b56)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

## OUTPUT:
![5 10](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/781b0095-fd39-4094-876f-dda3c8e827e7)

use 11
Or:
use auxiliary/scanner/mysql/mysql_version

## OUTPUT:
![eht 5 11](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/8cbdecb0-f91f-49c4-957a-8775ddb1a9ad)

Use the set rhosts command to set the parameter and run the module, as follows:

## OUTPUT:
![eht 5 12](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/88240250-15be-48cd-b58a-0474e541e0f1)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

## OUTPUT:
![eht 5 13](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/884057f1-ead6-4c80-b006-a226c32e4f23)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
  
## OUTPUT:
![eht 5 14](https://github.com/Javith-farkhan/Metasploit-for-reconnaissance/assets/94296805/9ca844f4-a356-43f5-b7e7-14d52792b3b9)

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
