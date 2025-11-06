# XSS — Super Short Intro 

## What is Cross-Site Scripting (XSS)?
XSS is a client-side web vulnerability where an application includes untrusted data in a page that is later interpreted as code by users’ browsers. A successful XSS allows an attacker to run JavaScript in the victim’s context, impersonate the victim, perform actions on their behalf, and access data available to the victim (for example session tokens, form data or DOM content). XSS variants include reflected, stored (persistent) and DOM-based — the difference is where the unsafe insertion happens (server response vs. stored data vs. client-side JS).

## Very short examples

### Reflected XSS (simple)
If a search page reflects a parameter directly into HTML, a payload like:

<script>alert(1)</script>


reflected in the response will execute in the visitor’s browser when they open the crafted link.

### Stored XSS (comment / profile)
If a comment or profile bio is saved to the database and later rendered without sanitization, a script saved there runs for every user who views that page.

### DOM-based XSS
Client JS reads location.hash or location.search and inserts it into the page with innerHTML / document.write. Visiting:

`https://example.com/#<img src=x onerror=alert(1)>`


can cause the injected fragment to execute if the page writes the hash into the DOM unsafely.

Attribute / URL context
When user input becomes an attribute value (e.g. href), attackers may use javascript: or event handlers to trigger code on click:

<a href="javascript:alert(1)">click me</a>


(Use simple alert(1) payloads during learning to confirm execution without harmful side effects.)

### Why XSS matters (one line)

XSS enables attackers to act as real users: steal tokens, perform actions, pivot to privileged workflows and maintain persistence in sessions — even when the server itself wasn’t directly compromised.
