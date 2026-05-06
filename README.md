<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# 🖥️ osTicket Installation & Configuration (Azure Virtual Machine)

---

## 📌 Project Summary

This project provides a step-by-step visual walkthrough of deploying the osTicket help desk system using a Microsoft Azure Virtual Machine.

The objective was to build a fully functional help desk environment by configuring a web server, installing required dependencies, setting up a database, and deploying the osTicket application from scratch.

---

### 🧰 Technologies & Environments Used

- Microsoft Azure Virtual Machine  
- Windows 11 Pro (Virtual Machine)  
- Windows 10 (Local machine for Remote Desktop access)  
- osTicket (Help Desk Ticketing System)  
- Internet Information Services (IIS)  
- PHP  
- MySQL  
- HeidiSQL  
- Remote Desktop Protocol (RDP)  
---

## 🔧 Step 1: Create and Configure Azure Virtual Machine



<img width="1415" height="1223" alt="01-AzureVM-Creation" src="https://github.com/user-attachments/assets/307c2491-4293-4678-96d2-f90256c0cd83" />



- Logged into Azure to begin setup.  
- Created a Virtual Machine and new Resource Group named **osTicket**.  
- Named the VM **osticket-vm** and set region to **Central US**.  
- Selected image: **Windows 11 Pro (x64 Gen2)**.  
- Selected size: **Standard_D2s_v3 (2 vCPUs, 8GB RAM)**.  



<img width="1415" height="1311" alt="02-AzureVM-Creation" src="https://github.com/user-attachments/assets/e5051871-a01f-4556-9540-1dac156273ba" />



- Set credentials:  
  - Username: `labuser`  
  - Password: `osTicketPassword1!`

⚠️ In real-world environments, secure and unique credentials must always be used.



<img width="1418" height="1315" alt="03-AzureVM-Creation" src="https://github.com/user-attachments/assets/26e763b5-fccd-4eb5-869d-bb2b1dfb3dd6" />



- Created a Virtual Network named **osticket-vm-vnet**.  
- Deploying VM by clicking **Review + Create → Create**.

---

## 🔧 Step 2: Connect using Remote Desktop



<img width="1389" height="1438" alt="04-ConnectingtoRDP" src="https://github.com/user-attachments/assets/3ec468b0-c133-4df4-82d5-bed12fca9334" />



- Opened **Remote Desktop Connection** by opening the Windows key, then typing Remote Desktop Connection.  
- Copied VM **Public IP Address** and pasted it.  



<img width="1418" height="978" alt="05-ConnectingtoRDP" src="https://github.com/user-attachments/assets/4fc1b5d4-4b8b-4dcf-baf2-59f986e2659e" />




- Logged in using lab credentials:  
  - Username: `labuser`  
  - Password: `osTicketPassword1!`  
  
⚠️ In real-world environments, secure and unique credentials must always be used.

- Successfully accessed the VM desktop.

---

## 🌐 Step 3: Enable IIS and CGI



<img width="828" height="398" alt="06-EnablingIIS_CGI" src="https://github.com/user-attachments/assets/8cb5647f-f336-46e7-be69-ca5008c7bffd" />



- Open Control Panel inside the VM, then click **Uninstall a Program**



<img width="834" height="336" alt="07-EnablingIIS_CGI" src="https://github.com/user-attachments/assets/6717089d-288f-4668-95fb-5dd4b9a543c4" />




<img width="445" height="416" alt="08-EnablingIIS_CGI" src="https://github.com/user-attachments/assets/8c742991-660b-4cee-94c9-1ed32bec982a" />



- Select **Turn Windows features on or off**.  
- And then enable:
  - Internet Information Services (IIS)  
  - CGI (under Application Development Features)  
- Apply changes.

---

## 📥 Step 4: Download and Extract osTicket Files



<img width="354" height="115" alt="09-osTicket-Installation" src="https://github.com/user-attachments/assets/40690ff4-6ee8-4501-9fe1-cf632e3a976a" />




- Download the osTicket-Installation-Files.zip inside the VM.  



<img width="169" height="278" alt="10-osTicket" src="https://github.com/user-attachments/assets/d5b88f82-2094-4892-9ed8-94cb701d17d8" />



- Save file to Desktop.  
- Extract using **Extract All**.

---

## 🐘 Step 5: Install PHP



<img width="832" height="419" alt="11-PHP-installation" src="https://github.com/user-attachments/assets/d773d8f9-d12e-49a0-8e16-fda69090b14c" />



- Create folder: `C:\PHP`.



<img width="732" height="221" alt="12-PHP-installation" src="https://github.com/user-attachments/assets/ede40b1e-b59d-42bc-a5ce-d817dd34bdc3" />



- Extract PHP files into `C:\PHP`.
- Verify `php-cgi.exe` exists.



<img width="1041" height="470" alt="13-PHP-installation" src="https://github.com/user-attachments/assets/5df53b8e-7bb9-47c4-94ed-62e043260031" />


  
- Install **PHP Manager for IIS**.

---

## 🧩 Step 6: Install Dependencies



<img width="1041" height="544" alt="14-vc_redist__rewrite_module-installation" src="https://github.com/user-attachments/assets/40a36c5d-6a94-4fa6-9d0c-6573bf840914" />



- Install:
  - VC_redist.x86  
  - rewrite_amd64_en-US  

---

## 🗄️ Step 7: Install and Configure MySQL



<img width="1044" height="556" alt="15-mysql-installation" src="https://github.com/user-attachments/assets/5f3a9ca7-81e0-491b-b195-4c8e9a9582c5" />
<img width="605" height="476" alt="16-mysql-setup" src="https://github.com/user-attachments/assets/beac18b6-ef01-4761-8650-eafcffe8cbdc" />
<img width="609" height="472" alt="17-mysql-setup" src="https://github.com/user-attachments/assets/63183e60-06eb-46bd-b3df-ce0b5c719fca" />



- Install MySQL 5.5.62.  
- Select **Typical Setup**.  
- Complete installation.



<img width="610" height="460" alt="18-mysql-configuration" src="https://github.com/user-attachments/assets/914b1e9b-dfe9-4c15-8917-f0b7237388e2" />
<img width="610" height="464" alt="19-mysql-configuration" src="https://github.com/user-attachments/assets/63601b59-0d90-432d-936b-9e72190cb1f8" />



- Select **Standard Configuration**.  
- Enable:
  - Install as Windows Service  



<img width="615" height="460" alt="20-mysql-configuration" src="https://github.com/user-attachments/assets/d9d0c0e2-989b-44db-8b7f-c622a5bcb8f2" />
<img width="615" height="473" alt="21-mysql-configuration" src="https://github.com/user-attachments/assets/b5c59a52-943d-480f-9d03-af42b18e008a" />



- Set credentials:
  - Password: `root`  
  - Confirm Password: `root`
  
⚠️ In real-world environments, secure and unique credentials must always be used.


- Complete configuration

---

## ⚙️ Step 8: Register PHP in IIS



<img width="1255" height="659" alt="22-PHPregIIS" src="https://github.com/user-attachments/assets/0702416f-1862-4c16-a226-3c6676fa6c88" />
<img width="1249" height="653" alt="23-PHPregIIS" src="https://github.com/user-attachments/assets/6d726ef4-7d51-43b0-9647-c5fdbef57e1d" />



- Open IIS Manager.  
- Navigate to PHP Manager.  
- Register PHP:
  - `C:\PHP\php-cgi.exe`

---

## 📁 Step 9: Deploy osTicket Files



<img width="1313" height="547" alt="24-deployosTicket" src="https://github.com/user-attachments/assets/c933c689-8cec-47dc-a468-8ae189669e22" />
<img width="1255" height="709" alt="25-deployosTicket" src="https://github.com/user-attachments/assets/90d040cf-c994-4038-963e-2afeb1a3ed09" />



- Open extracted osTicket-Installation-Files.  
- Copy **upload** folder.  
- Paste into:
  - `C:\inetpub\wwwroot`  
- Rename to **osTicket**.

---

## 🌐 Step 10: Open osTicket in Browser



<img width="1256" height="1149" alt="26-access_osTicket" src="https://github.com/user-attachments/assets/c1a541c8-4911-42a9-a5a8-20e326c2c92f" />



- Open a browser inside the VM.  
- Navigate to:
  - http://localhost/osTicket  
- Verify the setup page loaded.

---

## ⚙️ Step 11: Rename Config File and Set Permissions



<img width="1254" height="699" alt="30-ost-configuration" src="https://github.com/user-attachments/assets/46862344-f575-4585-bc03-3668097dabe5" />



- Navigate to:
  - `C:\inetpub\wwwroot\osTicket\include`  
- Rename:
  - `ost-sampleconfig.php` → `ost-config.php`



<img width="1251" height="806" alt="31-ost-configuration" src="https://github.com/user-attachments/assets/eff2a1f5-8faf-4332-a6f0-b14d9f20a4e6" />
<img width="1246" height="802" alt="32-ost-configuration" src="https://github.com/user-attachments/assets/7f6aaf47-8a58-4f7d-bb34-e2627e702b05" />
<img width="1139" height="768" alt="33-ost-configuration" src="https://github.com/user-attachments/assets/bc809374-862d-4933-8c80-dbf2d0a0afcc" />



- Open file properties by right-clicking the ost-config.php → Security Disable → inheritance
- Add:
  - **Everyone → Full Control**  

---

## 🔌 Step 12: Enable PHP Extensions



<img width="1250" height="656" alt="27-PHPextensions" src="https://github.com/user-attachments/assets/372751d3-0923-46e1-b25d-f5ca13264d4a" />
<img width="1255" height="659" alt="28-PHPextensions" src="https://github.com/user-attachments/assets/1038d13e-7bf7-4868-9686-2de34550f9e3" />



- Open PHP Manager.  
- Enable:
  - php_imap  
  - php_intl  
  - php_opcache  



<img width="251" height="850" alt="42-restartiis" src="https://github.com/user-attachments/assets/a023b3fc-d7ba-42da-a76e-62c311e55ffc" />



- Restart IIS (Stop → Start).  



<img width="717" height="369" alt="29-PHPextensions" src="https://github.com/user-attachments/assets/9441b729-2051-4162-b315-841b30cb90c4" />



- Refresh:
  - http://localhost/osTicket  



<img width="1460" height="764" alt="43-browser" src="https://github.com/user-attachments/assets/080c7df0-b032-42b5-b4e8-6ea40014e2d6" />



---

## 🗄️ Step 13: Create Database (HeidiSQL)



<img width="1253" height="704" alt="34-heidisql-setup" src="https://github.com/user-attachments/assets/3dfb35c4-8214-44dc-8ee5-1b5c6e345c48" />
<img width="1164" height="894" alt="35-heidisql-setup" src="https://github.com/user-attachments/assets/096fea60-ce26-4157-9f4b-0a29a5cbed97" />



- Open HeidiSQL.



<img width="1009" height="712" alt="36-heidisql-setup" src="https://github.com/user-attachments/assets/c41fd92f-4f5e-4ff8-af8f-5560aacfc212" />



- Create a new session named **osTicket**.  
- Enter credentials:
  - Username: `root`  
  - Password: `root`  

⚠️ In real-world environments, secure and unique credentials must always be used.

---

## ⚙️ Step 14: Complete Installation



<img width="1216" height="1061" alt="37-osTicket-setup" src="https://github.com/user-attachments/assets/89adf004-6547-468d-a3a3-e637a97fafeb" />
<img width="1212" height="623" alt="38-osTicket-setup" src="https://github.com/user-attachments/assets/5bd36602-e62e-4f6a-9a0b-e71f778cc37f" />



- Enter:
  - Database: `osTicket`  
  - Username: `root`  
  - Password: `root`
 
- Click **Install Now**.
 
⚠️ In real-world environments, secure and unique credentials must always be used.


<img width="1248" height="955" alt="39-osTicket-setup" src="https://github.com/user-attachments/assets/b499f887-3ebd-45c9-85f1-d98905eb7ffc" />






<img width="1040" height="1062" alt="40-osTicket-login" src="https://github.com/user-attachments/assets/191ae45b-5264-42ed-874a-4249b175180a" />
<img width="1038" height="619" alt="41-osTicket-login" src="https://github.com/user-attachments/assets/f5f1a00f-7107-44ce-980f-b2d6b6e5aea6" />



- Installation completed successfully.

- For Admin Login:
  http://localhost/osTicket/scp/login.php

- For End User Portal:
  http://localhost/osTicket
---


## ✅ Final Result

osTicket is successfully installed and running.  
The help desk system is fully operational.

---
