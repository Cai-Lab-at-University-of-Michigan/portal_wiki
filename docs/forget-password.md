---
tags: 
   - password
   - login
---

*Reset a forgotten password by email.*

---

## Steps

1. On the login page, click `Forgot Password?`.
2. Enter your `Email` and click `Continue`. A message confirms that a recovery email was sent.
3. Open the email and click `Reset password`.
4. On the `Reset Password` page, enter `New Password` and `Confirm Password`, then click `Reset Password`.
5. You return to the login page. Log in with the new password.

---

## Troubleshooting

- **No email arrives**: check spam or junk. `Request failed (500)` means the email could not be sent, and the site may have no mail set up. Ask the site administrator to set a new password.
- **`The user with this email does not exist in the system.`**: check the spelling and capital letters. The email must match the registered address exactly.
- **`Invalid token` after opening the link**: the link has expired or is incomplete (an email program can cut a long link). Request a new one.
- **`Inactive user` when saving the new password**: the account has not been activated yet. Ask the site administrator.

---

## Next

- To change a password you remember, use the `Security` tab in `Settings`. See [Navigation and Settings](navigation.md).
- Back to [Login](login.md).
