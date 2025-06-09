<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>🧰 Environments & Technologies Used</h2>

- **Microsoft Azure (Virtual Machines)**
- **Remote Desktop Protocol (RDP)**
- **Active Directory Domain Services (AD DS)**
- **PowerShell & PowerShell ISE**

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

1. 🏗️ Install and Configure Active Directory on DC-1
2. 👤 Create and Use Domain Administrative Accounts
3. 🔗 Join Client-1 to the Domain and Enable Remote Desktop Access
4. 🧑‍💻 Bulk User Creation and Login Testing

<h2>📌 Four High-Level Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/goWmUli.png" height="80%" width="70%"
</p>

1. 🏗️ Install and Configure Active Directory on DC-1

- Installed **Active Directory Domain Services (AD DS)** on the DC-1 VM.
- Promoted DC-1 to a **Domain Controller** using the domain: `mydomain.com`.
- Restarted and logged in as: `mydomain.com\labuser`.
<br />

<p>
<img src="https://i.imgur.com/WdEdfyI.png" height="80%" width="70%"
</p>

2. 👤 Create and Use Domain Administrative Accounts

- In **Active Directory Users and Computers (ADUC)**:
  - Created an Organizational Unit (OU) named `_EMPLOYEES`.
  - Created another OU named `_ADMINS`.
  - Created a domain admin account:
    - **Username:** `jane_admin`  
    - **Password:** `Cyberlab123!`
  - Added `jane_admin` to the **Domain Admins** security group.
- Logged out and back in as: `mydomain.com\jane_admin` (used for all future tasks).
<br />

<p>
<img src="https://i.imgur.com/U1HfktH.png" height="80%" width="70%"
</p>

3. 🔗 Join Client-1 to the Domain and Enable Remote Desktop Access

- Verified that Client-1 used **DC-1’s private IP as its DNS** (already configured in Azure).
- Joined `Client-1` to the domain `mydomain.com`.
- In ADUC:
  - Created a `_CLIENTS` OU and moved Client-1 into it.
- On `Client-1`:
  - Enabled **Remote Desktop**.
  - Allowed **Domain Users** to access Remote Desktop.
  - Confirmed non-admin users could now remotely log in.
<br />

<p>
<img src="https://i.imgur.com/5n50S00.png" height="80%" width="70%"
</p>

4. 🧑‍💻 Bulk User Creation and Login Testing

- Logged into DC-1 as `jane_admin`.
- Opened **PowerShell ISE** as administrator.
- Executed a provided PowerShell script to:
  - **Bulk-create users** in the `_EMPLOYEES` OU.
- Verified user creation in ADUC.
- Attempted to **log into Client-1 as one of the new users**, confirming successful authentication.
<br />

💼 Skills Demonstrated

- Active Directory deployment in cloud environments
- Azure VM networking and DNS configuration
- Domain controller setup and administration
- OU and user/group management in ADUC
- Remote Desktop setup for domain users
- PowerShell scripting and automation
- Real-world domain join troubleshooting and user testing
