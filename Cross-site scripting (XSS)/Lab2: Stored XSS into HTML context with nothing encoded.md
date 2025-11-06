# Lab2: Stored XSS into HTML context with nothing encoded

In Stored XSS, an attacker puts a special piece of text into that box and the site saves it. Later, when other users load the page, the site inserts the saved text into the page as-is.

the browser will see a real <script> tag and run it — a small popup appears. alert(1) is harmless and only proves that code execution is possible.

Because the site stores the malicious text, every user who visits the page can trigger the script.

If the attacker knows what they’re doing, they could make the injected script run on events like onmouseover (when a user moves their mouse over something) and use that to run JavaScript that exfiltrates sensitive data such as cookies or session tokens — which can lead to account takeover. (This is why alert(1) is used only as a safe proof-of-concept.)

<img width="899" height="664" alt="image" src="https://github.com/user-attachments/assets/f50b9ae8-5c7f-45a7-b882-304fdce3b083" />
