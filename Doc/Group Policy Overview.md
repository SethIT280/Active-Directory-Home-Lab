## Creating a Group Policy

### Option 1: Create and link to an OU in one step

1. Open **Group Policy Management** on the domain controller.
2. Expand your **Forest** and **Domain**.
3. Right-click the OU you want the policy to apply to.
4. Select **Create a GPO in this domain, and Link it here...**
5. Name the GPO, then right-click it and select **Edit** to configure the settings.
<img src="/Images/GroupPolicy1.png" width="600" alt="GroupPolicy1">
<img src="/Images/GroupPolicy2.png" width="600" alt="GroupPolicy2">
<img src="/Images/GroupPolicy3.png" width="600" alt="GroupPolicy3">

### Option 2: Create the GPO first, link it later

Use this if you don't want to tie the policy to a specific OU yet.

1. In **Group Policy Management**, expand **Group Policy Objects**.
2. Right-click the container and select **New**.
3. Name the GPO and configure its settings.
4. When you're ready, right-click the target OU and select **Link an Existing GPO...**, then choose the GPO.
<img src="/Images/GroupPolicy4.png" width="600" alt="GroupPolicy4">
<img src="/Images/GroupPolicy5.png" width="600" alt="GroupPolicy5">
<img src="/Images/GroupPolicy7.png" width="600" alt="GroupPolicy7">
<img src="/Images/GroupPolicy8.png" width="600" alt="GroupPolicy8">


---

## Testing a Group Policy

Run these steps on a **client device** that is joined to the domain and sits in the OU the GPO is linked to.

1. Open **Command Prompt**.
2. Run:

```cmd
   gpupdate /force
```

   This forces the client to resync with the domain controller and pull down any new or updated policies.

3. Restart the client. Some policies, such as computer-based settings, only apply after a restart or a fresh sign-in.
4. Confirm the policy took effect.


# List of Group Policies

- [Default Domain GPO](https://github.com/SethIT280/Active-Directory-Home-Lab/blob/main/Doc/GP%20Folder/Default%20Domain%20GPO.md)
- [ShortCut GP](https://github.com/SethIT280/Active-Directory-Home-Lab/blob/main/Doc/GP%20Folder/ShortCut%20GP.md)
