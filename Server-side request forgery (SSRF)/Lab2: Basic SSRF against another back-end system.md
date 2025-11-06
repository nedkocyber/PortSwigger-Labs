# Lab2: Basic SSRF against another back-end system

I start by intercepting the request and spot a parameter called `stockApi`. It looks like a public API call, but the value is URL-encoded and points to a non-existent domain.

<img width="1034" height="578" alt="image" src="https://github.com/user-attachments/assets/5d02df4c-1e67-458f-bd17-5cce920b652a" />

I drop the encoded value into CyberChef and decode it. Turns out it’s a full URL

<img width="1047" height="491" alt="image" src="https://github.com/user-attachments/assets/06b726e1-a5aa-4d5f-9552-eaec748947b2" />

Knowing the admin panel is likely on the same subnet, I fire up Burp Intruder and fuzz the last 8 bits of the IP — from `192.168.0.1` to `192.168.0.255`

<img width="1051" height="583" alt="image" src="https://github.com/user-attachments/assets/45e451bc-a2de-4f62-bee8-e8b1691e362a" />

<img width="1048" height="251" alt="image" src="https://github.com/user-attachments/assets/97bec4d4-8e88-43a4-93ea-801e0033c03b" />
For IP `192.168.0.94` I get a 200 OK response. Jackpot.

I manually probe `http://192.168.0.94/admin` via SSRF and get a response that looks like an admin interface. No login prompt. No auth. Why? Because the request is made by the server itself, and it trusts its own network.

<img width="520" height="363" alt="image" src="https://github.com/user-attachments/assets/4e4c34ad-d84f-47bf-a59a-7a976d88cf3e" />

<img width="824" height="217" alt="image" src="https://github.com/user-attachments/assets/68291ed6-3a25-4140-90af-cbdfb1dee478" />

I copy the admin panel link and paste it into my browser. I try to delete the user  manually — but the request fails. The browser isn’t authorized.

I right-click the "Delete" button, inspect the element, and find the endpoint `/admin/delete?username=carlos`

<img width="844" height="790" alt="image" src="https://github.com/user-attachments/assets/0cf5837e-8b41-4e1c-9194-c1f67a15035c" />

<img width="1049" height="258" alt="image" src="https://github.com/user-attachments/assets/ac4fe915-fb7b-4ea8-a0d5-f45158e1dec3" />

We inject this path into the `stockApi` parameter, trigger the internal request, and successfully delete the user — lab complete.

<img width="1043" height="428" alt="image" src="https://github.com/user-attachments/assets/3da33cac-b20a-4974-9c7d-ac064b10ae46" />
