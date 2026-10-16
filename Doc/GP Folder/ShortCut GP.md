# Shortcut Group Policy

This group policy will add shortcuts onto the desktop of computers within the Win11 PC OU.

**Path:** `Computer Configuration > Preferences > Windows Settings > Shortcuts`

---

## Add a New Shortcut

1. Right-click in the Shortcuts view.
2. Select ***New***.
3. Select ***Shortcut***.

<img src="/Images/ShortCutGP1.png" width="600" alt="ShortCut GP linked to the Win11 PC OU with the Shortcuts preference open">

<img src="/Images/ShortCutGP2.png" width="600" alt="Creating a new shortcut preference item">

---

## URL Shortcut Configuration

- **Action:** `Create`
  - Creates the shortcut if it does not already exist.
  - If you need to change the shortcut later, you must set the action to something else, like `Replace`.
- **Name:** `Youtube`
  - This is the name shown under the shortcut on the desktop.
- **Target type:** `URL`
  - This tells the shortcut to open a website.
- **Location:** `All Users Desktop`
  - This places the shortcut in `C:\Users\Public\Desktop` so it shows up on the desktop of every user on the PC.
- **Target URL:** `https://www.youtube.com`
  - The website the shortcut opens.
- **Shortcut key:** `None`
  - Allows the user to open the shortcut with a key combination like `Ctrl+7`.
- **Icon file path:** `%SystemRoot%\System32\SHELL32.dll`
- **Icon index:** `135`
  - Sets the icon to the image at index 135 in the .dll file.

<img src="/Images/ShortCutGP3.png" width="600" alt="Youtube shortcut properties in the ShortCut GP">

---

## Test

The client now has the YouTube shortcut.

<img src="/Images/ShortCutGP4.png" width="600" alt="Youtube shortcut on the desktop of USER-PC-1">

<img src="/Images/ShortCutGP5.png" width="600" alt="Youtube shortcut inside C:\Users\Public\Desktop">
