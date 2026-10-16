# Installing and Configuring DHCP

## Post-Installation Configuration

- Ran the **Complete DHCP configuration** wizard in Server Manager.
- This created the **DHCP Administrators** and **DHCP Users** security groups, which allow users with those roles to manage the DHCP server.
- It also authorized the DHCP server in Active Directory, which allows it to hand out addresses to devices in the domain.

<img src="/Images/DHCP1.png" width="600" alt="Complete DHCP configuration wizard">

# Creating the Scope

In **DHCP Manager**, expand the server, right-click **IPv4**, and select **New Scope**.

## IP Address Range

- **Start IP address:** 10.0.2.1
- **End IP address:** 10.0.2.254
- **Subnet mask:** 255.255.255.0
- The DHCP server leases addresses within this range to devices on the network.
- The subnet mask defines which part of the address identifies the network and which part identifies the device.

<img src="/Images/DHCP3.png" width="600" alt="Scope IP range and subnet mask">

## IP Exclusions

- **Exclusion range:** 10.0.2.1 - 10.0.2.10
- Exclusions prevent the DHCP server from handing out addresses in the specified range.
- This prevents IP conflicts and leaves room for devices with static IPs, such as the DC and switches.

<img src="/Images/DHCP4.png" width="600" alt="Exclusion range">

## Lease Duration

- **Duration:** 8 days (default)
- The lease duration determines how long a device keeps its IP address before it has to renew it.
- When a device leaves the network, its address returns to the pool once the lease expires, which prevents the pool from filling up with old devices.

<img src="/Images/DHCP5.png" width="600" alt="Lease duration">

## Domain Name and DNS Servers

- **Parent domain:** AGNB.lab
- **DNS server:** 10.0.2.10
- This sets the DNS server and domain suffix that DHCP gives to clients.
- Pointing clients at the DC's IP for DNS is what allows them to find the domain.

<img src="/Images/DHCP6.png" width="600" alt="Domain name and DNS servers">

# Testing

After finishing the scope, devices on the network get their network configuration from DHCP.

The DC keeps its static IP, but its DNS was changed to a loopback address, since it is now its own DNS server.

<img src="/Images/DHCP8.png" width="600" alt="DC network configuration with loopback DNS">

The client now gets its IP configuration from DHCP.

<img src="/Images/DHCP7.png" width="600" alt="ipconfig /all output on the Win11 client">
