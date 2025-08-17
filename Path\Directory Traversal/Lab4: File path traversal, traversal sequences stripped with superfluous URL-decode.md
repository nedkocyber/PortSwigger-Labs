# Lab4: File path traversal, traversal sequences stripped with superfluous URL-decode

We try a standard path traversal payload

<img width="517" height="30" alt="image" src="https://github.com/user-attachments/assets/52ac7662-fa3e-4b3a-b4da-5f1a77cf48c5" />

The request is blocked, as the application detects ../ sequences.

We encode the / character as %2f

<img width="834" height="256" alt="image" src="https://github.com/user-attachments/assets/3de0723c-f798-46e8-8453-434e13f9d55f" />

The server decodes it back to ../../, recognizes the traversal attempt, and blocks the request again.

Encode the already encoded / once more (%2f → %252f)

<img width="1022" height="527" alt="image" src="https://github.com/user-attachments/assets/63577f66-da8c-4823-8285-c98f342698d6" />

On the first decoding pass, %252f becomes %2f.
On the second decoding pass, %2f becomes /.
The application filter only catches the raw ../ sequence, so this bypass works.
