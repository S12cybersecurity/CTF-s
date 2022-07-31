# LAZY HACTHEBOX

**NMAP**

![image](https://user-images.githubusercontent.com/79543461/181914220-c170b5ef-4497-4782-a850-ee64e2866856.png)

In images directory i found this image:

![image](https://user-images.githubusercontent.com/79543461/181914359-4f48a689-911d-4b69-b40f-7c43babe1117.png)

I don't find ANYTHING...

But at one point I decide to see cookies, I see a cookie saved with the name auth, I'm going to try to change the cookie with the Burpsuite repeater and I get this error "Invalid Padding"...

Looks like a Padding Oracle Attack i try with Padbuster

**PADBUSTER**

https://github.com/AonCyberLabs/PadBuster

![image](https://user-images.githubusercontent.com/79543461/181920832-d23d94ef-48e4-40b0-92ab-614fb957a17d.png)

It seems that this is it!

![image](https://user-images.githubusercontent.com/79543461/181920870-f559dd10-cd40-4844-bfe2-cb76c21edb74.png)

DONE :)

It's the moment to create the cookie for admin user:

![image](https://user-images.githubusercontent.com/79543461/181921102-dd9bb793-28ad-48f1-a013-3a6a4d3e72ba.png)

I have the cookie!

![image](https://user-images.githubusercontent.com/79543461/181921111-7104b501-7014-4119-99e4-4c20f9765462.png)

I put in request and...

![image](https://user-images.githubusercontent.com/79543461/181921172-4ddc9da5-fdad-4517-8d4a-bc6b5a510453.png)

I'm in Admin account i have SSH id_rsa:

![image](https://user-images.githubusercontent.com/79543461/181921202-16659575-dc80-411a-9c09-8db75c278998.png)

I try to connect with SSH:

![image](https://user-images.githubusercontent.com/79543461/182016999-560c11a4-2784-452a-85cf-87389c4bc4c0.png)

I can execute script named backup with root permisions

I see string from this script and i see cat /etc/shadow

This is Path Hijacking...

cd /tmp

nano cat

![image](https://user-images.githubusercontent.com/79543461/182017810-0daddfc5-52cb-4d7f-9bdb-c46aac590166.png)

![image](https://user-images.githubusercontent.com/79543461/182017832-5ad76730-7fe4-4423-8e6d-9f2e5eed72e4.png)

I execute and i have root shell.

THANKS.

