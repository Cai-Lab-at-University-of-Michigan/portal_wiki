---
tags: 
   - login
---

*Create an account and sign in to the portal.*

---

## Sign up

1. Open <{{PORTAL_URL}}/login>.
2. Click `Sign Up`, under the login form.
3. Enter `Full Name`, `Email`, `Password` and `Confirm Password`, then click `Sign Up`.

You return to the login page without a message. The new account stays inactive until a site administrator activates it, so send the site administrator the email address you used.

---

## Log in

1. Open <{{PORTAL_URL}}/login>.
2. Enter your `Email` and `Password`, then click `Log In`.

You land on the `Dashboard`.

`Continue with Google` and `Continue with ORCID` sign you in through those services. They work only on sites configured for them, and a first sign-in creates an account that a site administrator must still activate.

To sign out, open the account menu in the top right (it shows your name, or `User` if none is set) and choose `Log Out`. On a narrow window, open `Open Menu` and choose `Log Out`.

---

## Troubleshooting

- **`Request failed (400)` with `Inactive user`**: the account has not been activated yet. Ask the site administrator.
- **`Incorrect email or password`, but the password is right**: the email is matched exactly. Capital letters before the `@` count, and the part after the `@` is stored in lower case. Type the same capitals before the `@` as at sign-up, and lower case after it.
- **`Request failed (400)` with `The user with this email already exists in the system`** when you sign up: the address is registered. Log in, or use `Forgot Password?`.
- **A message that the account is not active yet after `Continue with Google`**: the same cause as `Inactive user`. Ask the site administrator.
- **You are sent back to the login page**: the session has ended. Log in again.
- **Forgot the password**: see [Forgot Password](forget-password.md).

---

## Next

- [Navigation and Settings](navigation.md)
- [Uploads](file-uploads.md)
