# Lab1: Limit overrun race conditions

We begin by logging into the application using the provided credentials:`wiener:peter`

<img width="1047" height="512" alt="image" src="https://github.com/user-attachments/assets/1314d993-2844-4421-b103-f394e2f69eca" />

We add a product to our cart and apply a 20% discount code. The discount is meant to be applied only once per item.

<img width="522" height="277" alt="image" src="https://github.com/user-attachments/assets/49aa8e26-300d-4db0-bd0f-c65d7d2a8ec7" />

Using Burp Suite, we intercept the request that applies the discount. The request includes the discount code and product ID.
We prepare to exploit the race condition by sending this request multiple times in parallel.

<img width="1042" height="554" alt="image" src="https://github.com/user-attachments/assets/127db075-efbc-42e8-85d3-45e677253369" />

Just because 5 requests are not enough we make more and we add them to a group

<img width="999" height="539" alt="image" src="https://github.com/user-attachments/assets/59af6006-4ace-4171-9c29-707ab9b96922" />

We send the discount request several times using Burp’s grouped repeater with parallel execution enabled.
This floods the server with simultaneous discount requests — before it has time to lock or validate the cart state.

<img width="1381" height="653" alt="image" src="https://github.com/user-attachments/assets/53c2ceec-2940-4923-91ed-52a7b36a3af5" />

The server responds to multiple requests, and the discount is applied more than once — reducing the final price far beyond the intended limit.
This confirms the race condition vulnerability

<img width="942" height="419" alt="image" src="https://github.com/user-attachments/assets/3c21db02-c631-4d8f-9a05-e74bdbbaee84" />


