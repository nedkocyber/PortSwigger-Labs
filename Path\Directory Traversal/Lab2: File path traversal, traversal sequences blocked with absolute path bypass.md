# Lab2: File path traversal, traversal sequences blocked with absolute path bypass


After capturing the web request, we tested by injecting the path to /etc/passwd and successfully retrieved its contents. This confirms that the parameter does not properly validate or restrict user-supplied paths, leading to a path traversal vulnerability.

<img width="1045" height="562" alt="image" src="https://github.com/user-attachments/assets/602b276e-ed3f-4014-9b95-a163744c6ffe" />

