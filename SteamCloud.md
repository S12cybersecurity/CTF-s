# SteamCloud HACKTHEBOX

**ENUMERATION**

**NMAP**

![image](https://user-images.githubusercontent.com/79543461/179359903-10aab520-7f53-4057-8c5e-eaefd152cb4f.png)

When you can see this is a kubernetes machines

**Let's try to use kubectl**

![image](https://user-images.githubusercontent.com/79543461/179359961-cab6cb56-0ff2-492e-80fb-a9d2226faa19.png)

I don't have credentials.

**Let's try with kubeletctl**

![image](https://user-images.githubusercontent.com/79543461/179360830-ecb6cb85-1f76-4371-bd33-fe68567ef374.png)

Nice i recivied pods from Kubelets

I try to gain RCE in any pod

![image](https://user-images.githubusercontent.com/79543461/179361941-7ac48c14-b455-49e9-8f88-006a0bd81f7b.png)

Nginx and Kube-Proxy are injectables

I try with nginx and next Kube-Proxy

I have shell in nginx!

![image](https://user-images.githubusercontent.com/79543461/179361993-8aa44ce9-845a-401f-924d-17dc3bcf0488.png)

**Hacktricks**

https://book.hacktricks.xyz/cloud-security/pentesting-kubernetes/kubernetes-enumeration

![image](https://user-images.githubusercontent.com/79543461/179362094-7e69420c-5e7c-4c55-836e-8e95f3d64d0f.png)

I try to see Token an Certificate

I have all:

![image](https://user-images.githubusercontent.com/79543461/179362142-377dfa45-cb23-47a3-b3f2-18cdc9a3c5f0.png)

**Look that**

![image](https://user-images.githubusercontent.com/79543461/179362729-f5f3f120-0dc8-4071-9955-aae31c7e2969.png)

**Let's list privilieges**

![image](https://user-images.githubusercontent.com/79543461/179362874-ddf661e6-8be3-418b-b63f-4fb7924b1aa5.png)

I can create new pod!!

I copy same structuere 

![image](https://user-images.githubusercontent.com/79543461/179364596-8e746a8b-c2b0-48b4-972d-3445f87f76f0.png)

![image](https://user-images.githubusercontent.com/79543461/179364830-31c62ba5-7568-42e6-bf31-dda8ed8415f6.png)

I comprove:

![image](https://user-images.githubusercontent.com/79543461/179364870-00bbfc88-f43b-4e44-a9d8-0f6a5e662cbc.png)

**Perfect!!**

I gain shell:

![image](https://user-images.githubusercontent.com/79543461/179364984-fb10ac6d-948b-4dec-b90e-0c05bfddcba3.png)

![image](https://user-images.githubusercontent.com/79543461/179364998-e5f9ee10-3d79-4a7a-a97a-ee877e4cd927.png)

DONE :)
