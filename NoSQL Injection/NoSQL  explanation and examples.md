# What is NoSQL?
NoSQL is a type of database that stores data differently than traditional SQL databases. Instead of using tables and rows like Excel, NoSQL often uses documents (like JSON), key-value pairs, or graphs.
Popular NoSQL databases include:
• 	MongoDB
• 	CouchDB
• 	Redis
• 	Firebase

# What is NoSQL Injection?
Imagine you’re asking a librarian for a book by saying:

But instead, you say:

If the librarian doesn’t check your request properly, they might actually do it.
That’s NoSQL Injection — tricking a NoSQL database into doing something dangerous by sending it a sneaky query.

# How is NoSQL Injection Different from SQL Injection?


| Feature          | SQL Injection                           | NoSQL Injection                              |
| ---------------- | --------------------------------------- | -------------------------------------------- |
| Database Type    | Relational (tables, rows)               | Non-relational (documents, key-value, etc.)  |
| Query Language   | SQL (Structured Query Language)         | Depends on DB (e.g., MongoDB uses JSON-like) |
| Injection Format | Text-based (e.g., `' OR '1'='1`)        | Often JSON-based (e.g., `{ "$ne": null }`)   |
| Common Targets   | MySQL, PostgreSQL, MSSQL                | MongoDB, CouchDB, Firebase, etc.             |
| Typical Exploits | Dump data, bypass login, modify records | Same goals, but different syntax             |


