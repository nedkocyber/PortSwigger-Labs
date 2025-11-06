# SQL Injection

## What is SQL Injection (SQLi)?
SQL Injection is a vulnerability that occurs when an application embeds untrusted user input directly into an SQL statement. It can happen anywhere user-supplied data is used to build queries (URL parameters, form fields, headers, cookies). By manipulating that input, an attacker can change the intended SQL logic to read, insert, update or delete data, execute multiple statements, or escalate an attack to full system compromise if the database account has high privileges. Common vectors include concatenated strings, dynamic queries, and insufficient input handling.

### Very short examples

Auth bypass (simple)
Vulnerable pseudo-code:

`query = "SELECT * FROM users WHERE username = '" + user + "' AND password = '" + pass + "'";`


If user =` ' OR '1'='1` → condition becomes always true and the attacker may log in.

### Data leak (union)
Attacker appends a UNION to return other data:

`' UNION SELECT null, version(), null -- `


This can expose DB info or other rows.

### Modify data (UPDATE/DELETE/INSERT)
If the app executes multiple statements or concatenates input into an executable query, an attacker can change records:

`'; UPDATE users SET is_admin = 1 WHERE username = 'alice'; --`


Or delete data:

`'; DELETE FROM orders WHERE id = 1; --`


These payloads inject SQL that updates or removes rows, demonstrating how SQLi can lead to direct data modification (not only reading).

Blind (boolean) SQLi
When errors are hidden, you still probe logic via true/false conditions and infer data from page behavior (... AND 1=1 vs ... AND 1=2).
