# TRYHACKME OSCP PREP 3

**Offset**

fuzzer.py

![image](https://user-images.githubusercontent.com/79543461/177730350-66a7811c-44d7-4f89-b015-ace1ea60172b.png)

Crash:

![image](https://user-images.githubusercontent.com/79543461/177730238-49e5bdcf-a101-4119-9b4d-9b1de2b996d3.png)

Program crash with 1300

I recommend put 400 bytes more than crasher.

Create pattern:

![image](https://user-images.githubusercontent.com/79543461/177731933-3d132cda-40a4-46b6-9198-c7797411e00a.png)

Put in payload of exploit.py:

![image](https://user-images.githubusercontent.com/79543461/177732035-764d9a45-717f-47fc-a7b9-08e64ba69b32.png)

Offset Discover

![image](https://user-images.githubusercontent.com/79543461/177731773-026d3fd9-4fad-4564-9ca5-f88615844f3a.png)

Let's put EIP Register with BBBB its same than 42424242 in Hex.

