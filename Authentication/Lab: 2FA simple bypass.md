# Lab: 2FA simple bypass

We begin by logging in with the provided credentials for the victim:

<img width="278" height="59" alt="image" src="https://github.com/user-attachments/assets/52a7bfeb-fa18-43e6-ae1a-306cfd9c87a7" />

After submitting the login form, the application redirects us to a second step at , where it expects a 2FA security code.

We access the built-in email client provided in the lab environment. There, we find the 2FA code sent to carlos and use it to complete the login process.
This confirms that the 2FA mechanism is working — but we’re about to bypass it

<img width="520" height="227" alt="image" src="https://github.com/user-attachments/assets/f29449ba-a5b4-4e85-ab83-062699d5eae8" />

<img width="523" height="229" alt="image" src="https://github.com/user-attachments/assets/dc5910a2-df25-4fe9-8539-ce609304a9f9" />

After successful login, we notice that the URL contains a query parameter like:`/my-account?id=wiener`
This suggests that the user’s identity is being passed via a GET parameter, which may be vulnerable to tampering.

<img width="511" height="280" alt="image" src="https://github.com/user-attachments/assets/42217103-540b-422d-9ec8-9ac785b9968e" />

We log in again — but this time, after passing the first login step, we modify the id parameter in the URL from:`?id=wiener` to `?id=carlos
`

<img width="501" height="226" alt="image" src="https://github.com/user-attachments/assets/bc0ab7bf-a53b-4e53-99c8-01f768b961b6" />

By manipulating the  parameter after the first login step, we bypassed the 2FA check and accessed the victim’s account. The lab is successfully completed.

<img width="514" height="229" alt="image" src="https://github.com/user-attachments/assets/55be48db-4ce7-4a4c-b5aa-27167a751825" />








