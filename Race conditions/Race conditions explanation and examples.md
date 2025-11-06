# What is a Race Condition?

Imagine two kids racing to grab a 1-dollar bill from their mom. If they both reach her hand at the same time, she might get confused and accidentally give each of them a dollar — even though she only had one.
That’s a race condition: two or more actions happening at the same time, and the system doesn’t handle it properly — leading to unexpected or unsafe results.

# In Tech Terms
A race condition happens when:
• 	Multiple requests hit the server at the same time
• 	The server tries to process them without locking or checking properly
• 	This leads to duplicate actions, bypassed limits, or inconsistent data

# Real-World Examples
💸 Example 1: Double Withdrawal
A banking app lets users withdraw money. Normally, you can only withdraw once per minute.
But an attacker sends two requests at the exact same time: `POST /withdraw 
                                                              Amount: $100`

If the server doesn’t lock the account properly, both requests go through — and the attacker gets $200, even though they only had $100.

