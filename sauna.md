# SAUNA HACKTHEBOX

**DEMO**

https://youtu.be/KEU1l4OyYZ8

**ENUMERATION**

**NMAP**

![image](https://user-images.githubusercontent.com/79543461/178007053-6ad5df2a-9c74-4d28-bd2f-3cabb359a315.png)

**Kerberos User Enum**

![image](https://user-images.githubusercontent.com/79543461/178008296-118c1989-4b68-4af3-b127-e9d4683832fd.png)

**User fsmith don't need password let's go to crack it!**

![image](https://user-images.githubusercontent.com/79543461/178009159-487a2451-d289-460c-98ad-701227b7710e.png)

I copy hash you can see in last screenshoot and i put in hash file.

![image](https://user-images.githubusercontent.com/79543461/178009567-be7efa7d-8d29-4974-80ea-190889c72c35.png)

**I have first credentials!**

Comprove credentials:

![image](https://user-images.githubusercontent.com/79543461/178010039-eba0242d-d146-4091-93fb-b3190c221646.png)

**Let's go!!**

SecretsDump don't work:

![image](https://user-images.githubusercontent.com/79543461/178010706-3463db86-1805-4484-8d3e-0a7d7f7f2740.png)

**GetUsersSPN**

![image](https://user-images.githubusercontent.com/79543461/178011276-71ebf1fe-9ee0-45c9-bb13-16ba6b854046.png)

This means i can generate a ticket for user hsmith

![image](https://user-images.githubusercontent.com/79543461/178012090-2b39e6e7-8c28-4967-9dd6-3dc63ef05094.png)

But no works

**It's moment to connect to winrm**

![image](https://user-images.githubusercontent.com/79543461/178015837-e4f3ac11-f972-4f01-8745-639262b9eec5.png)

I run WinPEASx64.exe, i recomended this tool, its amazing: https://github.com/carlospolop/PEASS-ng/

I found credentials with WinPEAS.

![image](https://user-images.githubusercontent.com/79543461/178027809-3c8c16c5-5044-41a5-8e19-ae7f520b8e57.png)

Put the real username and the credentials are valid.

![image](https://user-images.githubusercontent.com/79543461/178029545-36c85bd2-c94e-4d61-b00d-6982e05420ab.png)

I use secretsdump:

![image](https://user-images.githubusercontent.com/79543461/178029960-de3c5f48-7c3f-4be3-866f-71f3116cd326.png)

**WORKS!!!**

I try to do Pass the Hash with admin account.

![image](https://user-images.githubusercontent.com/79543461/178030220-d2555101-61d5-46ea-98d1-23435e92e5b9.png)

**PWNED!!**

![image](https://user-images.githubusercontent.com/79543461/178030411-ef9a1287-ae9f-4f3d-9ba6-3605757db265.png)

DONE 

**DEMO**

https://youtu.be/KEU1l4OyYZ8

Thanks

