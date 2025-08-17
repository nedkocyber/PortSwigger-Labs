# Lab5: File path traversal, validation of start of path


<img width="1365" height="672" alt="image" src="https://github.com/user-attachments/assets/7e379e55-9efd-4d9e-9702-1a21f8686673" />

We were able to retrieve the contents of /etc/passwd because the filename parameter only validates that the path begins with /var/www/images.
It does not enforce any further checks on the remaining input, allowing us to append traversal sequences after the base path and escape the intended directory.
