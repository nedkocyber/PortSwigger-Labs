# What is XML?
XML is a way computers store and share data — kind of like a digital recipe book. It uses tags like:
```
<user>
  <name>RandomName</name>
</user>
```
# What is XXE Injection?
Imagine you give a robot a recipe, and you sneak in a line that says:

If the robot doesn’t check carefully, it might actually do it.
That’s XXE — tricking an XML parser into loading something dangerous, like a file from the server or a remote resource.

# Simple Example
Let’s say a website accepts XML input like this:

```
<user>
  <name>Target</name>
</user>
```
But an attacker sends this instead:
```
<?xml version="1.0"?>
<!DOCTYPE user [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<user>
  <name>&xxe;</name>
</user>
```
What happens?
• defines a shortcut called  that loads a file from the server.
• uses that shortcut.
• The server replaces  with the contents of the file — and sends it back to the attacker.
Sensitive data leaked.

