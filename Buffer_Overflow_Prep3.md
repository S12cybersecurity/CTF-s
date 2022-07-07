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

![image](https://user-images.githubusercontent.com/79543461/177735597-d290fd18-2a0c-4b02-bd27-cffe155dda81.png)

I run exploit:

![image](https://user-images.githubusercontent.com/79543461/177736959-02e6a8cf-6e5f-4e62-80c2-105709421b9a.png)

**BadChars**

!mona bytearray -b "\x00"

![image](https://user-images.githubusercontent.com/79543461/177737428-e47a158d-7692-4216-becc-b74d5f379552.png)

I put payload in exploit.py:

![image](https://user-images.githubusercontent.com/79543461/177737862-70f73c89-7797-4a31-a069-68dff9cfa191.png)

I run exploit:

!mona compare -a esp -f bytearray.bin

![image](https://user-images.githubusercontent.com/79543461/177738334-07d1d860-b0a5-4183-8bab-3c5bd5a82a27.png)

BadChars are:

\x00\x11\x40\x5f\xb8\xee

Comprove:

!mona bytearray -b "\x00\x11\x40\x5f\xb8\xee"

I put in exploit and i run exploit:

0 badchars!!

![image](https://user-images.githubusercontent.com/79543461/177740166-d6d5c807-7d29-4ea6-879f-acb6e84e23f8.png)

!mona jmp -r esp -cbq "\x00\x11\x40\x5f\xb8\xee"

I choose first jmp:

![image](https://user-images.githubusercontent.com/79543461/177740586-5691c8fa-f8e8-42d5-9e5a-7fe840ab72cb.png)

I put in retn with little-endian:

![image](https://user-images.githubusercontent.com/79543461/177741115-8292ab02-5905-4af6-b614-27addd946059.png)

