# osTicket Prerequisites and Installation Guide

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>

This guide provides a comprehensive overview of the prerequisites and installation process for osTicket, an open-source help desk ticketing system.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Protocol (RDP)
- Internet Information Services (IIS)

<h2>Operating System Utilized</h2>

- Windows 10 (21H2)

<h2>Prerequisites</h2>

- Establish a Remote Desktop Connection to the Virtual Machine
- Install and Enable IIS on Windows
- Install the Web Platform Installer
- Deploy osTicket v1.15.8
- Install HeidiSQL
- Configure the osTicket Database
- Adjust File Permissions

<h2>Installation Process</h2>

>**Note**: Before proceeding, download the required installation files 

### Step 1: Set Up a Virtual Machine in Microsoft Azure

Create a virtual machine (VM) in Microsoft Azure with Windows 10 as the operating system. Assign 2-4 vCPUs for optimal performance and designate a preferred name for the VM.

<br>
<p>
<img src="https://i.imgur.com/AIexboE.png" height="80%" width="80%" alt="VM Setup"/>
</p>
<br />

### Step 2: Connect to the Virtual Machine

Use `Remote Desktop Connection` to connect to the VM using its public IPv4 address.

<p>
<img src="https://i.imgur.com/5luMEbS.png" height="80%" width="80%" alt="Remote Desktop Connection"/>
</p>
<br />

### Step 3: Install the Web Platform Installer and Enable IIS

Access the `Control Panel`, navigate to **Programs**, and select **Uninstall a program**. Click **Turn Windows features on or off**, then enable `Internet Information Services (IIS)`. Additionally, enable `CGI` under **Application Development Features**.

<p>
<img src="https://i.imgur.com/a0HBeSB.png" height="60%" width="60%" alt="Programs"/> 
<img src="https://i.imgur.com/LgSXLgp.png" height="80%" width="80%" alt="Windows Features"/>
</p>
<br />

### Step 4: Install PHP and Dependencies

Download and install `PHP Manager` and the `rewrite module` from the provided installation files. Create a directory for `PHP` at `C:/PHP` and extract `PHP 7.3.8` into this folder. Additionally, install `VC_redist` and `MySQL 5.5.62`.

<p>
<img src="https://i.imgur.com/78HKcQK.png" height="80%" width="80%" alt="PHP Installation"/>
</p>
<br />

### Step 5: Configure MySQL

Once MySQL 5.5.62 is installed, configure the root password:
- Select **Typical Setup**
- Launch the **Configuration Wizard**
- Choose **Standard Configuration**
- Set up a root password

>**Tip**: Store usernames and passwords securely for later reference.

<p>
<img src="https://i.imgur.com/JKTxLB6.png" height="60%" width="60%" alt="MySQL Configuration"/>
</p>
<br />

### Step 6: Register PHP in IIS

Open `IIS` by searching for it in the Start menu and running it as an administrator. Double-click `PHP Manager`, then select `Register new PHP version`.

<p>
<img src="https://i.imgur.com/vYH68rW.png" height="70%" width="70%" alt="PHP Manager"/>
<img src="https://i.imgur.com/yrRjtSR.png" height="70%" width="70%" alt="Register PHP"/>
</p>
<br />

### Step 7: Deploy osTicket Files

Extract the osTicket installation package and move the `upload` folder to `C:\inetpub\wwwroot`. Rename `upload` to `osTicket`.

<p>
<img src="https://i.imgur.com/jpDaY1P.png" height="70%" width="70%" alt="osTicket Directory"/>
</p>
<br />

### Step 8: Configure IIS for osTicket

Restart IIS, navigate to **Sites** > **Default Web Site** > **osTicket**, and click **Browse * :80**.

<p>
<img src="https://i.imgur.com/atWUDVR.png" height="80%" width="80%" alt="IIS Configuration"/>
</p>
<br />

### Step 9: Enable Required PHP Extensions

In IIS, navigate to **Sites** > **Default Web Site** > **osTicket**, then open `PHP Manager`. Click **Enable or disable an extension** and activate `php_imap.dll`, `php_intl.dll`, and `php_opcache.dll`.

<p>
<img src="https://i.imgur.com/v4nZaF3.png" height="80%" width="80%" alt="PHP Extensions"/>
</p>
<br />

### Step 10: Update File Permissions

Rename `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php` to `C:\inetpub\wwwroot\osTicket\include\ost-config.php`, then modify its permissions to allow full access for all users.

<p>
<img src="https://i.imgur.com/UqGCKi0.png" height="80%" width="80%" alt="File Permissions"/>
</p>
<br />

### Step 11: Set Up the osTicket Database

Install `HeidiSQL`, create a new session using the root username and MySQL password, then create a new database named `osTicket`.

<p>
<img src="https://i.imgur.com/VBeqUTA.png" height="80%" width="80%" alt="HeidiSQL Setup"/>
</p>
<br />

### Step 12: Complete osTicket Installation

Return to the browser window with the osTicket installer, enter the required database credentials, and finalize the installation.

<p>
<img src="https://i.imgur.com/HYDWDu8.png" height="80%" width="80%" alt="Finalizing Installation"/>
</p>
<br />

### Step 13: Post-Installation Cleanup

To secure the installation, delete the `setup` folder in `C:\inetpub\wwwroot\osTicket` and set `ost-config.php` to **Read-only**.

<p>
<img src="https://i.imgur.com/OdagqtY.png" height="80%" width="80%" alt="Setting Read-Only Permissions"/>
</p>
<br />

<p align="right"> Proceed to <a href="[https://github.com/AlexisJ-Career/post-install-config]">OSTicket Post-Installation Configuration</a></p>
