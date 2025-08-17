# Lab3: File path traversal, traversal sequences stripped non-recursively.md

This lab is similar to the previous one, but with an additional layer of protection. Direct traversal attempts using ../../../ are filtered and removed. To bypass this, we can use an obfuscation technique such as ....//....//....//, which effectively bypasses the filter by breaking the detection logic that strips ../. This allows us to successfully retrieve the contents of /etc/passwd despite the implemented defense.

<img width="1041" height="642" alt="image" src="https://github.com/user-attachments/assets/6be4fc26-8dde-4245-9e10-5d1a08215748" />

