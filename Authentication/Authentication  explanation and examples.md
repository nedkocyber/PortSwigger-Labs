# What Is Authentication?
Authentication is how a system confirms who you are. It’s the process of verifying your identity before giving access to sensitive data or actions.
Common authentication methods include:
• 	Username + password
• 	One-time codes (2FA)
• 	Session tokens or cookies
• 	Biometrics (fingerprint, face scan)


# What Is an Authentication Vulnerability?
An authentication vulnerability means an attacker can pretend to be someone else — without knowing their real credentials. This can happen due to:
• 	Weak login logic
• 	Poor session handling
• 	Predictable tokens
• 	Missing rate limits
• 	Flawed password reset flows
• 	Race conditions

# Real-World Examples
## 1. Brute-Force Login
An attacker tries thousands of passwords for a known username (e.g. ) without being blocked:
```
POST /login
username=admin
password=123456
```
If there’s no rate limiting or CAPTCHA, the attacker may guess the correct password.

## 2. Predictable Tokens
If session or reset tokens are easy to guess:
```
GET /reset?token=abc123
```
And the next token is , the attacker can generate valid tokens and hijack accounts.

## 3. Password Reset Abuse
If the system lets you reset someone else’s password without proper verification:
```
POST /reset-password
username=carlos
new_password=hacked123
```
And no token or email confirmation is required — that’s a critical flaw

## 4. Race Condition in Login
The attacker sends multiple login attempts in parallel to bypass rate limits and brute-force the password faster:
• 	Turbo Intruder
• 	Parallel Repeater
• 	Look for 302 redirects (successful login)



