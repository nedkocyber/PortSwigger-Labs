# Lab1: Username enumeration via different responses

We start by loading a list of potential usernames. This will be used to fuzz the login form and detect which usernames exist based on how the server responds.

<img width="515" height="262" alt="image" src="https://github.com/user-attachments/assets/7ae2914c-4238-45da-8edc-3273a9444e2a" />

We intercept a login request and send it to Burp Intruder. We place the attack marker (§) in the username field and configure the payload with our wordlist.

<img width="425" height="247" alt="image" src="https://github.com/user-attachments/assets/67d32e2b-e895-479c-8b9e-1e38c86bc0c2" />

<img width="513" height="270" alt="image" src="https://github.com/user-attachments/assets/eae21718-3ab2-4a55-9350-ce73f9273664" />

As we run the attack, we observe the server’s responses:
- For most usernames, the server returns:
Invalid username
- For one specific username (pi), the response is different:
- The length of the response changes
- The error message changes to:
Invalid password
This confirms that pi is a valid username — the server leaks this information through inconsistent error messages.

<img width="526" height="239" alt="image" src="https://github.com/user-attachments/assets/4d77a423-32ce-4d34-9b5d-aa0af38e9b18" />

Now that we know pi is valid, we repeat the process — this time fuzzing the password field using a password wordlist.
We monitor the responses for a 302 status code, which indicates a successful login.

<img width="524" height="296" alt="image" src="https://github.com/user-attachments/assets/f4394068-8875-4bdf-bf28-cf140b361027" />

<img width="513" height="271" alt="image" src="https://github.com/user-attachments/assets/7255a21b-5e55-49ca-a4e2-48c824dbaf22" />

We find that the password dallas works for user pi. The server responds with a 302 redirect — confirming successful authentication.

<img width="483" height="168" alt="image" src="https://github.com/user-attachments/assets/08fae5d3-e43c-464c-b4d0-6b5d644a7132" />








