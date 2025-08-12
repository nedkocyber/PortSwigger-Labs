The first lab is preaty straith forward we capture the web request with burp suite to exploit it

<img width="1290" height="661" alt="image" src="https://github.com/user-attachments/assets/5e6d7c24-ef93-4a95-9ca5-bad8a43c6ba4" />

<img width="1046" height="578" alt="image" src="https://github.com/user-attachments/assets/af04e68e-e8af-4a1d-8eda-2d19cbda95cf" />

The Forward command sends the request further along the chain:

If it comes from the browser – it will be sent to the server.

If it comes from the server (in the HTTP response section) – it will be sent back to the browser.

Example:

You load a website in your browser.

Burp intercepts the request (if Intercept is turned on).

You see the request in the Proxy > Intercept tab.

Right-click > Forward ➜ the request is sent to the server (and the website continues to load).

If you want to make changes to the request, you do this before pressing Forward.


