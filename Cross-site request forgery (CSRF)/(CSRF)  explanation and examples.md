# What is CSRF?
Imagine you’re logged into your favorite game website. Now imagine someone sends you a link that secretly tells the game to delete your account — without you knowing.
That’s CSRF — tricking a logged-in user’s browser into doing something dangerous on a site they’re already authenticated with.

# In Tech Terms
CSRF happens when:
• You’re logged into a website (like your bank or email).
• You visit a malicious site or click a bad link.
• That site sends a request to the original site using your credentials (like cookies or session tokens).
• The original site thinks it’s you — and performs the action.

# Simple Example
Let’s say you’re logged into:`https://mybank.com`
And someone sends you a link like:`https://mybank.com/transfer?amount=1000&to=attacker`

And if your browser is still logged in, it might send that request automatically — and the bank transfers the money, thinking it was you.

