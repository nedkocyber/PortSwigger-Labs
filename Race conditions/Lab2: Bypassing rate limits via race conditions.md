# Lab2: Bypassing rate limits via race conditions


We’re given:
• 	A valid username: 
• 	A wordlist for brute-forcing the password
• 	A strict 15-minute time window before the lab environment resets and the password changes
The login endpoint has rate limiting, but we’ll bypass it using parallel requests.

<img width="513" height="318" alt="image" src="https://github.com/user-attachments/assets/dda462a0-fbbe-4581-bccf-6b1492c73800" />

We intercept a login request and prepare it for brute-force testing. Instead of manually sending each password attempt, we clone the request multiple times.
This allows us to simulate parallel login attempts — bypassing sequential rate limits

<img width="478" height="390" alt="image" src="https://github.com/user-attachments/assets/ad39b1db-c59c-46c3-b101-bdd472c6df6f" />


To automate and accelerate the attack, we use the Turbo Intruder extension in Burp Suite.
• 	We send the login request to Turbo Intruder
• 	Load the provided wordlist
• 	Modify the script slightly to match the lab’s login format
• 	Launch the attack

<img width="513" height="267" alt="image" src="https://github.com/user-attachments/assets/f0ab3d99-2cc4-418a-8bfb-5ed54d8e3608" />

To make the most out of Burp Intruder, you’ll need some Python skills — most payloads rely on it. If coding isn’t your strong suit, let ChatGPT fine-tune your scripts for you.

<img width="524" height="323" alt="image" src="https://github.com/user-attachments/assets/aa6b7ba0-9087-4c6c-b7d0-fc2f2f07c8ce" />

We monitor the responses for a 302 status code — this indicates a successful login (redirect after authentication).
Once we spot the 302, we know we’ve found the correct password.

<img width="473" height="327" alt="image" src="https://github.com/user-attachments/assets/31cf7be9-79a9-4138-96fd-ed5cfb54527b" />

Using the cracked credentials, we log in as wiener From the admin panel, we delete the user carlos — completing the lab.

<img width="510" height="151" alt="image" src="https://github.com/user-attachments/assets/ed172229-7684-48dc-b1a4-e96820ccaa5e" />



