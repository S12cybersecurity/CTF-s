# TRYHACKME OVERFLOW 2

**It's Windows 7 32 bits**

fuzzer.py:

![image](https://user-images.githubusercontent.com/79543461/177651167-3cb08660-7165-46f8-b1f9-9541d8fe5f96.png)

python3 fuzzer.py:

![image](https://user-images.githubusercontent.com/79543461/177651361-af07de68-fc30-4851-ab7c-1008109f9dae.png)

Crash at 700 bytes

I recomend use 300 bytes more to next step 700+300=1000

![image](https://user-images.githubusercontent.com/79543461/177653018-1f1f1f11-e2bf-4e7b-8942-8ce5f2509ad4.png)

exploit.py:

![image](https://user-images.githubusercontent.com/79543461/177651633-8178015a-6530-4b00-9623-2115f1376e61.png)

I put output from 1000 bytes in payload variable of exploit.py file.

I run exploit

![image](https://user-images.githubusercontent.com/79543461/177652086-ef416a63-1b49-4532-8291-4fa73842899c.png)

I copy EIP:

![image](https://user-images.githubusercontent.com/79543461/177653961-c7d4ef8f-abd0-44e0-be75-c8bc00b08952.png)

msf-pattern_offset -l 1000 -q 76413176

![image](https://user-images.githubusercontent.com/79543461/177728070-a400c61b-93fe-45cf-b8da-851c8b1489fa.png)



