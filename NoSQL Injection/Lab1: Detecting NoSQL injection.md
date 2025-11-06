# Lab1: Detecting NoSQL injection

I start by intercepting one of the requests related to product categories. The request includes a parameter that looks injectable — so I test it by adding a single quote () to break the syntax.

<img width="1234" height="649" alt="image" src="https://github.com/user-attachments/assets/ef36b1a9-85a5-4030-83ed-57acb04f81a2" />

After injecting the quote, the application throws an error. Not only does it confirm the input is unsanitized — it also reveals the backend database is MongoDB.
This is a strong indicator of a NoSQL injection point.

<img width="1033" height="455" alt="image" src="https://github.com/user-attachments/assets/499b5664-3de0-459d-85e0-ae4fe1fabd99" />

Now that I know the app is using MongoDB, I craft a basic NoSQL injection payload. Instead of using quotes or SQL-style syntax, I inject a JSON-like structure:

<img width="912" height="579" alt="image" src="https://github.com/user-attachments/assets/2a1604a7-3c3d-4d45-af14-0f106031ecde" />

And this is enough to compleate the lab.
