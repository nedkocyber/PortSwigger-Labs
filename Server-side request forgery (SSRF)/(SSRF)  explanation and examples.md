# What is SSRF?
Imagine you’re in a classroom, and you want to know what’s inside the teacher’s locked drawer. You can’t open it yourself — but you trick your friend (who has access) into opening it for you and telling you what’s inside.
That’s what SSRF is — tricking a server into making a request on your behalf to somewhere it normally shouldn’t go.

Simple Example
Let’s say there’s a website that lets you preview a profile picture by giving it a URL:

`https://example.com/fetch-image?url=https://images.com/cat.jpg`

The server takes that URL and fetches the image to show it to you.
But what if someone changes the URL to this:

`https://example.com/fetch-image?url=http://localhost:8000/admin`

Now the server is tricked into visiting its own private admin page, which the hacker can’t normally see — but the server can.
