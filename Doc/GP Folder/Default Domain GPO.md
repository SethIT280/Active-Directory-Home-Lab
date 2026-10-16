# Default Domain Policy

The Default Domain GPO is a pre-built GPO which is applied to the entire domain. For the purposes of my home lab I will be using it to control Password Policies, Account Lockout Policies, and Kerberos Policies.

---

## Password Policies

Password Policies focus on requirements for users' passwords.

**Path:** `Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Password Policy`

- **Enforce password history:** `24 passwords remembered`
  - This policy disallows users from re-entering any of their last 24 passwords.
- **Maximum password age:** `90 days`
  - This policy enforces users to reset their passwords within the entered number of days.
- **Minimum password age:** `1 day`
  - This stops users from changing their password repeatedly, which would make it easier to circumvent Enforce password history.
- **Minimum password length:** `12 characters`
  - This policy forces users to create passwords that are at least X amount of characters long. Longer passwords make brute force attacks less successful.
- **Minimum password length audit:** `Not Defined`
  - This logs an event when a user sets a password shorter than the audit value without blocking it, which lets you check who would not be compliant with an updated password policy.
- **Password must meet complexity requirements:** `Enabled`
  - This requires users to include at least 3 of the 4 character types (uppercase letters, lowercase letters, numbers, and special characters) within the password. This increases password complexity, making it harder for attackers to breach.
- **Relax minimum password length limits:** `Not Defined`
  - This policy allows the minimum password length to be set to more than 14 characters. The reason this policy exists is because some legacy devices can't handle more than 14 character passwords. For the purposes of my home lab I will keep it not defined for now.
- **Store passwords using reversible encryption:** `Disabled`
  - Stores passwords in a form the system can decrypt. It should only be used when dealing with legacy systems that need a plain text password to gain access.

<img src="/Images/GPDomainDefault9.png" width="600" alt="Final Password Policy settings in the Default Domain Policy">

<details>
<summary>Defaults and Changes</summary>

<img src="/Images/GPDomainDefault1.png" width="600" alt="Default Password Policy settings before changes">

<img src="/Images/GPDomainDefault2.png" width="600" alt="Setting Maximum password age to 90 days">

<img src="/Images/GPDomainDefault3.png" width="600" alt="Setting Minimum password length to 12 characters">

</details>

---

## Account Lockout Policies

Account Lockout Policies focus on the triggers for when a user account is locked out and when the lockout is reset.

**Path:** `Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy`

- **Account lockout duration:** `5 minutes`
  - This policy sets how long an account stays locked out after hitting the threshold. After that time the account unlocks automatically. This helps prevent others from brute forcing a user's account.
- **Account lockout threshold:** `5 invalid logon attempts`
  - This policy causes a user account to lock after X amount of failed login attempts. This helps prevent brute force attacks.
- **Allow Administrator account lockout:** `Not Defined`
  - This policy allows the admin account to be locked if too many attempts are made. I have this not defined for my lab, but in real world scenarios it can stop attackers from getting access to an admin role.
- **Reset account lockout counter after:** `5 minutes`
  - This policy resets the failed login attempt count to zero after X amount of time, so old failed attempts don't add up toward a lockout.

<img src="/Images/GPDomainDefault8.png" width="600" alt="Final Account Lockout Policy settings in the Default Domain Policy">

<details>
<summary>Defaults and Changes</summary>

<img src="/Images/GPDomainDefault4.png" width="600" alt="Default Account Lockout Policy settings before changes">

<img src="/Images/GPDomainDefault5.png" width="600" alt="Setting Account lockout duration to 5 minutes">

<img src="/Images/GPDomainDefault6.png" width="600" alt="Suggested Value Changes for lockout threshold and reset counter">

</details>

---

## Kerberos Policies

Kerberos is an authentication protocol that Windows uses for domain logins. This protocol allows users to gain access to domain resources without re-entering information.

**Path:** `Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Kerberos Policy`

- **Enforce user logon restrictions:** `Enabled`
  - This policy checks the user's restrictions every time a ticket is requested. This makes sure that a user's permissions are immediately removed instead of having to wait for the ticket to try to renew.
- **Maximum lifetime for service ticket:** `600 minutes`
  - This policy limits the amount of time a service ticket is valid.
- **Maximum lifetime for user ticket:** `10 hours`
  - This policy limits the amount of time a ticket-granting ticket (a ticket you get when you first log in that allows you to get service tickets) is valid.
- **Maximum lifetime for user ticket renewal:** `7 days`
  - The time that a TGT can be renewed without typing in a password.
- **Maximum tolerance for computer clock synchronization:** `5 minutes`
  - This policy will cause authentication to fail if the device's clock is off from the DC by more than X amount of time, preventing replay attacks.

<img src="/Images/GPDomainDefault7.png" width="600" alt="Kerberos Policy settings left at the defaults">

---

## Verification

```CMD
gpupdate /force
```
