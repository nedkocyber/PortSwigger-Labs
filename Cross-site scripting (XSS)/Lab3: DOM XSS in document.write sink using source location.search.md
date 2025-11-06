# Lab3: DOM XSS in document.write sink using source location.search.md

I start the lab quickly and purposefully — immediately opening Inspect to see where my input reflects in the DOM. I tested several URL parameters and noticed that  is used by the page, and  directly injects content without any sanitization.
In DevTools → Elements, I found the spot: there's an  element whose  value is populated from the URL parameter. This hinted at the type of payload I should try


<img width="1387" height="631" alt="image" src="https://github.com/user-attachments/assets/fd260bf3-f434-4cb6-8014-8b3b8daa8449" />

`">\<svg onload=alert(1)>`


<img width="1026" height="439" alt="image" src="https://github.com/user-attachments/assets/df62ae71-c0b5-4d24-a6c3-4609f5e192f7" />
