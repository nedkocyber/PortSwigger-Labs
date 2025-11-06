# Lab1: Basic SSRF against the local server

I start by intercepting the request and notice a parameter called `stockApi` Its value looks suspicious — possibly base64 or URL-encoded.

<img width="1031" height="549" alt="image" src="https://github.com/user-attachments/assets/e56eb766-8eb9-48e2-9c5b-1d04a9b5e77c" />

After decoding the value with CyberChef, I see it points to an internal API endpoint — something like:
That’s a red flag. This endpoint shouldn’t be exposed to the outside world

<img width="1038" height="490" alt="image" src="https://github.com/user-attachments/assets/371a6e65-77ea-434c-a5aa-e0cc0592458d" />

I tweak the `stockApi` parameter to point directly to the internal admin panel. Boom — the response shows an admin interface. No authentication required. Why? Because the request is made server-side, and the server trusts itself.

<img width="1047" height="623" alt="image" src="https://github.com/user-attachments/assets/9a6cac10-cf27-45a2-85c1-197a74bb19e4" />

I copy the admin panel link and paste it into my browser. But when I try to delete the user, I get blocked — the browser request isn’t authorized.

<img width="1038" height="539" alt="image" src="https://github.com/user-attachments/assets/6d37beb9-8e74-4893-abdd-6d8c62543052" />
<img width="1043" height="513" alt="image" src="https://github.com/user-attachments/assets/f1f765ec-fe81-44b5-920f-cd87ef2d33de" />

Hovering over the “Delete” button reveals the actual deletion path:

<img width="1080" height="637" alt="image" src="https://github.com/user-attachments/assets/038f7c06-aa28-46f9-889c-2bc0dfad0e82" />

Now that I know the exact path, I weaponize the  parameter. I change it to:`http://localhost/admin/delete?username=carlos`

<img width="1386" height="447" alt="image" src="https://github.com/user-attachments/assets/5ca1ced6-d734-4833-966f-df03821de443" />

