# Lab3: Password reset broken logic 

We begin by using the "Forgot Password" feature and submitting our own username (e.g., wiener). This triggers the password reset flow and generates a temporary token.

<img width="491" height="255" alt="image" src="https://github.com/user-attachments/assets/416f22cb-2340-4b6e-8aa7-e3aa10373637" />

<img width="514" height="209" alt="image" src="https://github.com/user-attachments/assets/3f274900-9310-44cc-a59c-2b1bf4ae4ed6" />

We intercept the password reset request and observe the following:
• 	A token field:

• 	A username field:

This suggests that the token is not bound to the username — a major flaw

<img width="504" height="261" alt="image" src="https://github.com/user-attachments/assets/c2ac1dc1-d316-4293-80c3-2c6b0ef68c70" />

We modify the username field in the intercepted request:


<img width="517" height="247" alt="image" src="https://github.com/user-attachments/assets/90ffa513-b934-4ec2-81f8-b2c5ee14ed3a" />

We send the request and receive a 302 status code, indicating the password was successfully changed — even though the token was generated for a different user.

<img width="509" height="237" alt="image" src="https://github.com/user-attachments/assets/6152f6b2-e11d-4141-9bd2-122ddc3b4443" />






