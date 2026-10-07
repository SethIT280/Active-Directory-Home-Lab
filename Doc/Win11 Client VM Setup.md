# VM Setup

- **Name:** Win11User_1
- **ISO:** Windows 11
- **Edition:** Windows 11 Pro (Pro is needed to connect to a domain)

<img src="/Images/EndUsersetup1.png" width="600" alt="Creating the Accounting OU">
<img src="/Images/EndUsersetup5.png" width="600" alt="Creating the Accounting OU">
## Resources

- **Memory:** 4 GB
- **CPU:** 2 cores
- **Storage:** 30 GB

<img src="/Images/EndUsersetup2.png" width="600" alt="Creating the Accounting OU">

<img src="/Images/EndUsersetup3.png" width="600" alt="Creating the Accounting OU">

# Creating a Local Account

- **Local account name:** IT Admin

<img src="/Images/EndUsersetup7.png" width="600" alt="Creating the Accounting OU">


Windows 11 forces you to sign in with a Microsoft account by default, which is not wanted when adding a Windows 11 device to a domain. To create a local account instead:

1. Press `Ctrl + Shift + F10` to open a command prompt.
2. Run `cd oobe`
3. Run `bypassnro.cmd`

<img src="/Images/EndUsersetup6.png" width="600" alt="Creating the Accounting OU">


This restarts the computer, and as long as it stays offline, setup will allow the creation of a local account.

# Network

The VM is using the same NAT Network as the DC, which allows it to connect to the domain and the internet.

<img src="/Images/EndUsersetup4.png" width="600" alt="Creating the Accounting OU">

## Client Network Configuration

- **IP address:** Automatic
- **Subnet mask:** 255.255.255.0
- **Default gateway:** 10.0.2.1
- **DNS:** Automatic

The IP address can change depending on which IP the DHCP server leases. Since the VM is on the same network as the DC running DHCP, the DNS server points to the DC's IP: 10.0.2.10. Having DNS point at the DC is what allows the VM to find and connect to the domain.

<img src="/Images/EndUsersetup12.png" width="600" alt="Creating the Accounting OU">

## Testing the Connection

Tested connectivity by pinging google.com.

<img src="/Images/EndUsersetup13.png" width="600" alt="Creating the Accounting OU">

# Adding the VM to the AGNB Domain

1. Go to **Settings** > **Accounts** > **Access work or school**.
2. Click **Connect**, then choose **Join this device to a local Active Directory domain**.
3. Enter the domain name and sign in.
4. Restart the computer.
<img src="/Images/EndUsersetup8.png" width="600" alt="Creating the Accounting OU">
<img src="/Images/EndUsersetup9.png" width="600" alt="Creating the Accounting OU">
<img src="/Images/EndUsersetup10.png" width="600" alt="Creating the Accounting OU">

After the restart, the device is connected to Active Directory and is placed in the default Computers container automatically.
 
