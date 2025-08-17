# Lab6: File path traversal, validation of file extension with null byte bypass


<img width="1286" height="629" alt="image" src="https://github.com/user-attachments/assets/9126b44f-e851-4fd4-bbd0-d5ecd7612360" />

The %00 character represents a null byte, which is commonly used in exploits against C- or PHP-based applications, where strings are terminated with \0. By appending .png after the null byte, we can bypass the application’s file extension validation.

If the application enforces that the filename ends with .png, we can set:

filename = ../../../etc/passwd%00.png

The server sees this as a valid .png file. However, if the application is vulnerable to null byte injection, the system ignores everything after the null byte. As a result, only ../../../etc/passwd is processed, allowing us to access the restricted system file while bypassing the extension check.
