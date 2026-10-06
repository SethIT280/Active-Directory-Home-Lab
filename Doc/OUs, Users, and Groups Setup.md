# Organizational Units

- Created an **Employees** OU with sub-OUs for the different departments: **IT**, **HR**, **Sales**, and **Accounting**. These sub-OUs hold user accounts separated by department.
- Created a **Win11 PC** OU to hold the computers I add to the domain.
- Setting up these OUs allows for organizing users, groups, and computers, and also for assigning Group Policy to them.

<img src="/Images/UsersAndOU1.png" width="600" alt="Employees OU with department sub-OUs">

<img src="/Images/UsersAndOU2.png" width="600" alt="Creating the Accounting OU">

# Creating Users

## Test User

- **Name:** John Smith
- **Logon name:** John.Smith@AGNB.lab
- **OU:** Employees/IT

<img src="/Images/UsersAndOU3.png" width="600" alt="Creating the test user John Smith">

## Password

- Set up the account with a temporary password.
- Checked "User must change password at next logon", which forces the user to change their password the first time they log in.

<img src="/Images/UsersAndOU4.png" width="600" alt="Password options for the new user">

# Admin Account

- **Name:** !SBoulanger
- **Logon name:** !SBoulanger@AGNB.lab
- **OU:** Employees/IT/IT Admin

<img src="/Images/UsersAndOU13.png" width="600" alt="Creating the admin account">

Setting up a separate admin account allows for the implementation of least privilege, separating daily tasks like email from administrative tasks like software installation.
