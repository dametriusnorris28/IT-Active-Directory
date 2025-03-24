# Active Directory Lab

<img width="817" alt="Screenshot 2025-03-24 at 1 14 53 PM" src="https://github.com/user-attachments/assets/07fb43be-4ce7-4bf1-8de8-52b85d6a08c9" />


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

<img width="956" alt="VirtualBox_DC" src="https://github.com/user-attachments/assets/67591e1e-da31-46a9-9fd6-01dd4a770741" />  
<img width="966" alt="client1_pc_virtualbox" src="https://github.com/user-attachments/assets/3ee7abc5-e22e-49b0-8132-456ece2e260c" />


---

## 🧷 Windows Server 2022 & AD Configurations

The Windows Server was configured with two network interfaces: one connected to the internet via my home router (Internet NIC), and one connected to an internal network (Internal NIC). The internal NIC was assigned a static IP address, with a loopback address (127.0.0.1) set for DNS to allow the server to resolve itself. The server's hostname was changed to **DC** before promoting it to a domain controller.

<img width="560" alt="Network_Connections" src="https://github.com/user-attachments/assets/a7cfe8bd-debf-4bb3-8888-6da08ab566b0" />
<img width="562" alt="NC_Details" src="https://github.com/user-attachments/assets/9d4e4fef-c424-4958-a866-ad891277cc30" />


---

## ⚙️ Roles & Services Installation

I installed and configured key Windows Server roles including Active Directory Domain Services (AD DS), DNS, DHCP, Remote Access (NAT), and IIS. Each role supports core network functions and collectively enable a fully functional domain environment.

<img width="814" alt="dashboard" src="https://github.com/user-attachments/assets/39d85ecf-d7e4-4f6d-a57d-46a7daafbdb9" />


- **Active Directory Domain Services (AD DS)** – Manages domain users, computers, and security policies. I created an organizational unit _ADMIN, and created an admin user.
- **DNS Server** – Resolves hostnames within the domain; critical for domain functionality.
- **DHCP Server** – Automatically assigns IP addresses to clients on the internal network.
- **Remote Access (NAT)** – Allows internal VMs to access the internet through the internet NIC. A virtual router was created in this setup.
- **Web Server (IIS)** – Installed for testing internal web hosting functionality.

---
### Adding Users to Active Directory
<img width="608" alt="PowerShell_create_users" src="https://github.com/user-attachments/assets/bdf64d8e-5a1c-4bf8-9807-47b3ac644dc9" />

Using a PowerShell script, I bulk-loaded **1,000 users** into Active Directory from a text file.

<img width="376" alt="Users_AD_list" src="https://github.com/user-attachments/assets/39150463-b178-434e-a180-f79aaf6395cc" />

Confirmation that the PowerShell script worked and the users were successfully added.

<img width="257" alt="self_admin_user" src="https://github.com/user-attachments/assets/dfa2998f-a103-4e2a-95eb-e67ae1b5896b" />

A search within Active Directory shows my custom user account added from the powershell script and the administrator account within Active Directory.

---

### Joining CLIENT1 PC TO DOMAIN
The Windows 10 client successfully joined the domain controlled by the DC. It received its IP address from the DHCP server and resolved the domain using the DNS service hosted on the DC.
<img width="419" alt="client1pc_foundon_DCserver_ad_dhcp" src="https://github.com/user-attachments/assets/59d86c7c-a693-45a9-9197-a9e788b9487d" />
<img width="508" alt="clientpc_ping_domain_internet" src="https://github.com/user-attachments/assets/0b4ec8b6-14b9-4707-b427-36fb32c5a5c6" />


CLIENT1 pc was able to ping the internet and domain successfully.

---

## 🧩 Conclusion

This lab provided a solid hands-on experience in setting up a Windows Server environment with core network services. I configured the server roles, established internal/external networking, and validated functionality by joining a client to the domain. This project strengthened my understanding of enterprise networking, directory services, and system administration fundamentals.

