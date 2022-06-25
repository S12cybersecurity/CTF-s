## VulnNet: Roasted:

****ENUMERATION****

**NMAP:**

I run NMAP to see all port in state open are in this machine:

![image](https://user-images.githubusercontent.com/79543461/175721449-95047f5c-dd39-4894-b5d0-0921391abda2.png)

**Kerbrute User Enum:**

I use UserEnum Module from Kerbrute to Enumerate users via Kerberos Open Service

![image](https://user-images.githubusercontent.com/79543461/175765882-a3e1b6fb-5aee-4ae0-a907-0c044979ffc4.png)

**Samba:**

I need to Enumerate de Shared Resources From This Domain.

![image](https://user-images.githubusercontent.com/79543461/175766359-e330d34e-0e87-427f-b195-36a9f462a0ff.png)

And This is Interesting, when machine have SMB open and IPC$ Open with Minium Read Access it's vulnerable to other User Enumeration.

Let's Go to See The Permisions of IPC$ with smbmap:

![image](https://user-images.githubusercontent.com/79543461/175766561-0a71ddff-470b-4c54-be8d-92ecbeca3717.png)

Read Permisions!!!

Let's Go to Enumerate Users:

![image](https://user-images.githubusercontent.com/79543461/175766742-f4fd3548-f094-45c9-92e1-48ee1323211c.png)

I put Only UserNames in the file users.txt

![image](https://user-images.githubusercontent.com/79543461/175767545-87cbbf76-64f5-4957-9124-61217876c426.png)

Now i go to see if any user don't have a good security authentication.

**GetNPUsers:**

![image](https://user-images.githubusercontent.com/79543461/175768575-c0c284fb-322e-4a9f-8966-53bb8416958b.png)

User "t-skid" have UF_DONT_REQUIRE_PREAUTH set!! 

**John The Ripper**

![image](https://user-images.githubusercontent.com/79543461/175768653-af07e116-b531-4892-96f1-57b876577d9f.png)

**Samba With t-skid User:**

![image](https://user-images.githubusercontent.com/79543461/175768898-4373df8b-5000-4d58-94d3-b58c10331cf4.png)

I enter to NETLOGON:

![image](https://user-images.githubusercontent.com/79543461/175768978-9faae125-2b8c-4ba7-9768-6ede418dd2d0.png)

**ResetPassword.vbs**

![image](https://user-images.githubusercontent.com/79543461/175769081-19b57b0e-e497-4cea-aa5d-53cd0201334b.png)

Credentials founded for a-whitehat User

Let'g Go to Connect Via evil-winrm:



