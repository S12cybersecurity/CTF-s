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
