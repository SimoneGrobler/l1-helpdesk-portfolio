# Ticket 001 — Password Reset

**Category:** Password/Account
**Priority:** Normal
**SLA:** Default (18hr grace period)
**Requester:** John Smith (Sales)
**Status:** Resolved

---

## Reported issue

John Smith, a Sales team member, submitted a ticket after returning from
leave stating he could not remember his Active Directory password and
was locked out of his workstation. He requested a password reset so he
could regain access.

> "Hi, I just got back from leave and can't remember my password to log
> into my computer. Can someone reset it for me? Thanks, John"

---

## Diagnostic steps

1. Reviewed the incoming ticket in the osTicket Open queue and assigned
   it to myself.
2. Before making any account changes, replied to the ticket requesting
   identity confirmation — standard practice before modifying any
   account, even in a low-friction lab environment, since password
   resets are a common social-engineering target in real helpdesk
   environments.
3. Once identity was confirmed, connected to the domain
   (`simonelab.local`) using OpenRSAT from the technician workstation.
4. Located John's account (`j.smith`) under the **Sales** organizational
   unit.

## Resolution

1. Used OpenRSAT's password reset function on the `j.smith` account and
   set a temporary password.
2. Enabled **"User must change password at next logon"** so John would
   be forced to set his own new password on first login, rather than
   continuing to use a password known to the technician.
3. Replied to the ticket confirming the reset was complete, without
   including the temporary password in the ticket thread itself — it
   was communicated through a separate channel, consistent with basic
   credential-handling hygiene.
4. Marked the ticket as **Resolved**.
5. **Verified the fix end-to-end** by logging into the end-user
   workstation as `j.smith` using the temporary password, confirming
   the forced password-change prompt appeared as expected, and
   successfully completing the change to a new, user-set password.

## Notes

- This was a deliberately low-complexity ticket, used to establish the
  baseline workflow for this portfolio: **submit → triage → verify
  identity → resolve → confirm fix → document.** Every ticket after
  this one follows the same shape.
- Verifying the fix from the end-user side (rather than stopping once
  the AD-side change was made) matters — a reset that looks correct in
  OpenRSAT isn't confirmed until the user can actually log in with it.
- No temporary credentials were ever placed in ticket text, matching
  standard credential-handling practice.

