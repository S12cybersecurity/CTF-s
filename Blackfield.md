# Blackfield HACKTHEBOX

**Enumeration**

**NMAP**

![image](https://user-images.githubusercontent.com/79543461/184364952-5f4b8a18-fdb9-4625-8017-c6ab7e78cfcf.png)

**AD ENUM**

My own tool: 
https://github.com/S12cybersecurity/AD-Pentest

I try to get users from this domain with module users

![image](https://user-images.githubusercontent.com/79543461/184396085-66a596a9-02d5-4e2e-9ba8-d958326c46bb.png)

RPC Blocked but LookUPSID works!!

![image](https://user-images.githubusercontent.com/79543461/184399086-71a6ac71-fea8-4819-9e20-36db50a5eb36.png)

ASREPRoasting attack!!

I have credentials:

![image](https://user-images.githubusercontent.com/79543461/184400122-3b1c29d2-2727-4138-b610-bc1e816fc455.png)

I can't access with EVIL-WINRM, i need BloudHound:

**Bloodhound**

![image](https://user-images.githubusercontent.com/79543461/184404307-26ead43c-6e0e-4ee5-a53b-599077afd4f2.png)

I upload in bloodhound GUI:

![image](https://user-images.githubusercontent.com/79543461/184404476-530943ae-fa42-4682-a02d-96c54441313e.png)

I put my user:

![image](https://user-images.githubusercontent.com/79543461/184404533-c956644f-686d-4dd4-a968-f71b577d5b43.png)

I can change password to audit2020 user:

![image](https://user-images.githubusercontent.com/79543461/184408474-0f3bd0e8-7f6d-4620-8a75-8c624ca1f312.png)

![image](https://user-images.githubusercontent.com/79543461/184408771-13b7c320-5b64-44a1-abaa-ac3bc347f7a2.png)

New password is 'Password123'

![image](https://user-images.githubusercontent.com/79543461/184409540-fbde289f-d338-44dc-9bd2-476c16e5d8c0.png)

I found new SMB Folders

![image](https://user-images.githubusercontent.com/79543461/184410794-7ab05878-0504-44f6-b634-801465d61df8.png)

I found one interesting file named lsass.zip

![image](https://user-images.githubusercontent.com/79543461/184410882-2581ae2c-5039-457b-9b0b-87cec344190a.png)

I run pypykatz and i found hash

![image](https://user-images.githubusercontent.com/79543461/184410949-b04c6fc6-92fc-473b-a516-fd9273929571.png)

I can connect with evil-winrm

![image](https://user-images.githubusercontent.com/79543461/184411071-2de4199a-15d9-4dcd-8495-4238d00f7591.png)

I have user.txt

![image](https://user-images.githubusercontent.com/79543461/184411189-d8bfcb47-4daa-401c-bd4d-bc0958d94dd2.png)

Privilieges...

![image](https://user-images.githubusercontent.com/79543461/184411327-56e8da27-d5f5-4817-823f-683180acbc33.png)

PERFECT!! SeBackupPriviliege...

