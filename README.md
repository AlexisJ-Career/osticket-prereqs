# osTicket - Prerequisites and Installation
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>


This tutorial provides a step-by-step guide on setting up the open-source help desk ticketing system, osTicket, including its prerequisites and installation.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Protocol (RDP)
- Internet Information Services (IIS)

## Operating Systems Used

- Windows 10 (21H2)

## Prerequisites

Before installation, ensure you have the following components ready:

- Internet Information Services (IIS)
- Microsoft Web Platform Installer
- osTicket v1.15.8
- PHP Manager
- MySQL 5.5 Database
- HeidiSQL Client
- Microsoft Visual C++ 2009 Redistributable

## Installation Steps

:exclamation: **Follow these steps in order, as errors may require starting over with a fresh virtual machine.** :exclamation:

### Step 1: Create and Configure a Virtual Machine

1. Create a Windows 10 (21H2) Virtual Machine in Microsoft Azure.
2. Connect to the VM using Remote Desktop Protocol (RDP).

### Step 2: Enable Internet Information Services (IIS)

1. Navigate to Control Panel → Programs → Turn Windows features on or off.
2. Enable **Internet Information Services (IIS)**.

(Screenshot 1)

### Step 3: Install Web Platform Installer and Required Components

1. Download and install **Web Platform Installer**.
2. Using Web Platform Installer, search for and install:
   - MySQL 5.5 Database
   - PHP 5.6.31
   - PHP (x86) versions 7.0 - 7.3

(Screenshot 2)
(Screenshot 3)

**Note:** During MySQL 5.5 installation, use `root` as the username and `Password1` as the password. Keep these credentials saved for later steps.

### Step 4: Install Additional Dependencies

If any installations fail, manually download and install:

- PHP 7.3.8
- PHP Manager
- Microsoft Visual C++ 2009 Redistributable

(Screenshot 4)

### Step 5: Download and Configure osTicket

1. Download **osTicket v1.15.8**.
2. Extract the files.
3. Copy the "upload" folder to `C:\inetpub\wwwroot` and rename it to `osTicket`.

(Screenshot 5)

### Step 6: Restart IIS and Launch osTicket

1. Open **Internet Information Services (IIS) Manager**.
2. Restart IIS.

(Screenshot 6)

3. In IIS, navigate to `Sites → Default → osTicket` and select **Browse *:80**.
4. A new browser window will open, displaying the osTicket setup page.

(Screenshot 7)

### Step 7: Configure PHP Extensions

1. In IIS, go to `Sites → Default → osTicket`.
2. Open **PHP Manager**.
3. Enable the following extensions:
   - `php_imap.dll`
   - `php_intl.dll`
   - `php_opcache.dll`

(Screenshot 8)

### Step 8: Refresh osTicket Setup Page

After enabling PHP extensions, refresh the osTicket setup page.

(Screenshot 9)

### Step 9: Modify Configuration File Permissions

1. Rename `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php` to `ost-config.php`.
2. Right-click `ost-config.php`, select **Properties → Security → Advanced**.
3. Click **Disable Inheritance → Remove**.
4. Add **Everyone** with **Full Control** permissions.

(Screenshot 10)
(Screenshot 11)

### Step 10: Finalize osTicket Installation

1. In the browser, proceed with the installation wizard.
2. Fill in the required fields:
   - **Help Desk Name:** Your Help Desk
   - **Default Email:** Any email (used for practice)
   - **Admin Credentials:**
     - Username: `user_admin`
     - Password: `Password1`
   - **MySQL Database Settings:**
     - Database: `osTicket`
     - Username: `root`
     - Password: `Password1`

(Screenshot 12)

Click **Install Now** to complete the installation.

(Screenshot 13)

### Step 11: Install and Configure HeidiSQL

1. Download and install **HeidiSQL**.
2. Open HeidiSQL and create a **New Session**.
3. Enter `root` as the user and `Password1` as the password.
4. Click **Open**.
5. Create a new database named `osTicket`.

(Screenshot 14)
(Screenshot 15)

### Step 12: Complete Setup in the Browser

1. Return to the browser.
2. Complete the final configuration and confirm installation success.

(Screenshot 16)

You will now have access to two URLs:

- **End-User Portal:** Where users submit tickets.
- **Staff Control Panel:** Where admins and support staff manage tickets.

(Screenshot 17)
(Screenshot 18)

### Step 13: Post-Installation Cleanup

1. Delete `C:\inetpub\wwwroot\osTicket\setup` folder.

(Screenshot 19)

2. Reset **Everyone**'s permissions for `ost-config.php` to **Read & Execute** only.

(Screenshot 20)

:tada: **Congratulations! You've successfully installed osTicket.** 🎉
