# Active Directory Lab

<img width="817" alt="Screenshot 2025-03-23 at 6 40 17 PM" src="https://github.com/user-attachments/assets/dec6ac99-9871-481b-8eec-0f2d17949c61" />

## 🧾 Introduction / Summary

This project demonstrates a simulated enterprise environment using Windows Server 2022 as a domain controller and a Windows 10 client machine. The goal was to configure core networking services such as Active Directory, DHCP, DNS, and Remote Access, while also simulating a NAT gateway setup. The lab was designed and hosted using VirtualBox with internal and external networking. This setup mirrors real-world small to medium business infrastructure and supports learning system administration and domain management.

---

## 🛠️ Technology & Components Used

- Windows Server 2022
- Windows 10
- Active Directory Domain Services (AD DS)
- DNS Server
- DHCP Server
- Remote Access / NAT
- PowerShell
- VMWare/VirtualBox Networking

---

## 💻 VirtualBox Setup

I created two virtual machines using VirtualBox. The first is a **Windows Server 2022** machine configured as the domain controller (DC). The second is a **Windows 10** machine (CLIENT1) which is used to join the domain and test connectivity.

![Screenshot](Attach Screenshot Here)  
![Screenshot](Attach Screenshot Here)

---

## 🧷 Windows Server 2022 & AD Configurations

The Windows Server was configured with two network interfaces: one connected to the internet via my home router (Internet NIC), and one connected to an internal network (Internal NIC). The internal NIC was assigned a static IP address, with a loopback address (127.0.0.1) set for DNS to allow the server to resolve itself. The server's hostname was changed to **DC** before promoting it to a domain controller.

![Screenshot](Attach Screenshot Here)  
![Screenshot](Attach Screenshot Here)

---

## ⚙️ Roles & Services Installation

![Screenshot - Roles Dashboard](Attach Screenshot Here)

- **Active Directory Domain Services (AD DS)** – Manages domain users, computers, and security policies. I created an organizational unit _ADMIN, and created an admin user.
- **DNS Server** – Resolves hostnames within the domain; critical for domain functionality.
- **DHCP Server** – Automatically assigns IP addresses to clients on the internal network.
- **Remote Access (NAT)** – Allows internal VMs to access the internet through the internet NIC. A virtual router was created in this setup.
- **Web Server (IIS)** – Installed for testing internal web hosting functionality.

---

![Screenshot - PowerShell Script](Attach Screenshot Here)

Using a PowerShell script, I bulk-loaded **1,000 users** into Active Directory from a text file.

![Screenshot - AD User List](Attach Screenshot Here)  
Confirmation that the PowerShell script worked and the users were successfully added.

![Screenshot - My User & Admin Accounts](Attach Screenshot Here)  
A search within Active Directory shows my custom user account added from the powershell script and the administrator account within Active Directory.

![Screenshot - Client1 Joining Domain](Attach Screenshot Here)  
The Windows 10 client successfully joined the domain controlled by the DC. It received its IP address from the DHCP server and resolved the domain using the DNS service hosted on the DC. The CLIENT1 pc was able to ping the internet and domain successfully.

---

## 🧩 Conclusion

This lab provided a solid hands-on experience in setting up a Windows Server environment with core network services. I configured the server roles, established internal/external networking, and validated functionality by joining a client to the domain. This project strengthened my understanding of enterprise networking, directory services, and system administration fundamentals.

