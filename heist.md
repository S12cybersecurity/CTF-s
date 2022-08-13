# HEIST HACKTHEBOX

**ENUMERATION**

**NMAP**

![image](https://user-images.githubusercontent.com/79543461/184477884-22fc3ac3-08df-410f-b1c7-0e7bb103b35c.png)

**WEB**

![image](https://user-images.githubusercontent.com/79543461/184477942-a4541eca-b461-41e4-b2e9-8d6d5a51319c.png)

I login as guest

![image](https://user-images.githubusercontent.com/79543461/184477955-b930c622-818e-4b71-b89f-eb1b460606a9.png)

I see this messages talking about problems with cisco router

![image](https://user-images.githubusercontent.com/79543461/184478061-4c62dca4-7efe-42d2-b2db-f52ff6451b74.png)

If you click in Attachment you can see intersting things:

![image](https://user-images.githubusercontent.com/79543461/184477979-133fdad0-8660-4454-b704-7ddc69b77f5d.png)

I copy and save this to my machine and i clone this repository to deecrypt cisco passwords:

https://github.com/theevilbit/ciscot7

I crack very easy the passwords:

![image](https://user-images.githubusercontent.com/79543461/184478161-df18ce8c-a7ab-48f0-94ba-025963046827.png)

This are the credentials:

![image](https://user-images.githubusercontent.com/79543461/184478220-7ce78dc2-02bf-4c10-9dd8-7118347fc4ad.png)

I create users.txt file with hazard (user from forum) admin (file) rout3r (file) 

And i create a passwords.txt witw both cracked passwords

Password Spryng:

![image](https://user-images.githubusercontent.com/79543461/184478405-5ff3168a-6a79-4637-a04a-111c883476d8.png)

0 results...

I go back to Hazard file and i see other hash:

![image](https://user-images.githubusercontent.com/79543461/184478441-a81f4ab1-0c49-47a4-8ced-b53ac8ac5135.png)

I try to crack it:

![image](https://user-images.githubusercontent.com/79543461/184478452-f6a005f3-b7c5-45cc-906e-41381d12b2eb.png)

Perfect, now i put in passwords file and i try other Password Sprying:

![image](https://user-images.githubusercontent.com/79543461/184478572-fa610160-d9b3-4659-8486-15d0c98e6243.png)

PERFECT!! I have credentials!

I try crackmapexec to test winrm to access to victim local machine bur anytthing:

![image](https://user-images.githubusercontent.com/79543461/184478646-743ab519-f723-498d-83cc-ca7677d5f42e.png)

New Resources:

![image](https://user-images.githubusercontent.com/79543461/184478684-cbdfb79f-2192-4f8d-a75e-f24eb1da45f4.png)

I can't access to RPC

But i have Read Permisions in IPC$ share smb resource

I can enumerate users with lookupsid.py from impacket python library

![image](https://user-images.githubusercontent.com/79543461/184478860-8569e32c-59db-4ac9-bf5b-b5638a717ced.png)

I do this regular expresion to save users in users.txt file:

![image](https://user-images.githubusercontent.com/79543461/184478918-736aac75-7937-45f6-b09a-b9bab310d91c.png)

I try other password spying and...

![image](https://user-images.githubusercontent.com/79543461/184478943-83a7a661-11dd-49c2-98d9-bf2e4126f8c8.png)

I have credentials to Chase user:

![image](https://user-images.githubusercontent.com/79543461/184478974-96c54d98-4964-4cdd-80e2-88b7d0738215.png)

I can access with evil-winrm to victim machine!

![image](https://user-images.githubusercontent.com/79543461/184479022-e7afeca2-eb30-4695-ac28-b2d53aee42f8.png)

I find this processes for firefox

![image](https://user-images.githubusercontent.com/79543461/184479322-9232d923-39b0-47ac-8152-fa15cae9f8ba.png)

I try to use procdump for 64 bits

I download from here:
https://docs.microsoft.com/en-us/sysinternals/downloads/procdump

I upload to victim machine

![image](https://user-images.githubusercontent.com/79543461/184479416-c9f9962a-d2f8-43c2-8bf9-4bad1748d133.png)

I search firefox process:

![image](https://user-images.githubusercontent.com/79543461/184479477-7b66042a-1720-4730-b5dc-16ad2caf6dbf.png)

I have dumped 

![image](https://user-images.githubusercontent.com/79543461/184479620-62d18569-9174-4a89-91db-0c6141a858f9.png)

I start to download this to my kali machine.

I do strings and i found password:

![image](https://user-images.githubusercontent.com/79543461/184479980-09781c6a-5711-44b2-a063-4df6a3028bde.png)

I have admin Creds!!

PWNED!!

![image](https://user-images.githubusercontent.com/79543461/184480073-6964469c-53d0-4e29-b991-871a8e6eb16e.png)

THANKS!

Video for this in this youtube channel:

https://www.youtube.com/channel/UCmMvgBYm3m53losIj2pE9jA
