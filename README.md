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
![image](https://github.com/user-attachments/assets/612af462-3cdd-4384-a5ab-8710b2e01a53)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:

<li>systemctl start postgresql</li>

<li>msfdb init</li>

Invoke msfconsole:


## OUTPUT:
![image](https://github.com/user-attachments/assets/3242a35a-9790-4b7c-9767-784f5b4737d4)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![image](https://github.com/user-attachments/assets/0a9ac61c-00d1-479b-8922-ad808d48777e)

Port Scanning: Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). 
```msf > nmap -sT 192.168.1810/24 -p1-1000```

## OUTPUT:
![image](https://github.com/user-attachments/assets/1ab5c73a-2c0a-4a72-a08d-7d42f32f1428)
#### step4: 
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. 
```msf > db_nmap 192.168.181.0/24```
## OUTPUT:
![image](https://github.com/user-attachments/assets/8e621b81-51fe-4695-94ba-fe59fd08d2bf)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. 
```cd /user/share /metasploit-framework/modules/auxiliary kali > ls -l```
## OUTPUT:
![image](https://github.com/user-attachments/assets/e6546036-ceff-4f93-b72c-663d98eba5dd)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
```msf >search name:Microsoft type:exploit```

## OUTPUT:
![image](https://github.com/user-attachments/assets/96646f3b-29c8-4cd0-98b5-1ce6f173d54f)

The info command provides information regarding a module or platform,
Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
<li>systemctl start postgresql</li>

<li>msfdb init</li>

### MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
```db_nmap -sV -sC -p 3306 <metasploitable_ip_address>```
![image](https://github.com/user-attachments/assets/dd581b9a-07b5-4efb-8928-f0350d17b781)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql
![image](https://github.com/user-attachments/assets/f6ec952b-8d60-4a17-ad5a-73bca7b86f22)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version
![image](https://github.com/user-attachments/assets/6378038f-63cb-4d7a-817d-9b1cb2f02ec1)

Use the set rhosts command to set the parameter and run the module, as follows:
![image](https://github.com/user-attachments/assets/b1fda6e7-96de-4035-b5e2-e1fd7b6c49e3)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
![image](https://github.com/user-attachments/assets/c2826347-ca65-4402-9916-4ef8564a4c43)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:

```set PASS_FILE /usr/share/wordlists/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS```

Set BLANK_PASSWORDS to true in case there is no password set for the root account.

```set BLANK_PASSWORDS true```

![image](https://github.com/user-attachments/assets/43c9f0c9-d674-4ecb-b534-1dab772a27d1)

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
