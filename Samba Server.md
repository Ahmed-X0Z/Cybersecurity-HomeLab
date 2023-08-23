# Samba Server
Introduction:  
In this documentation, we will guide you through the process of setting up a Samba server on an Ubuntu Server in your cybersecurity home lab project. The Samba server will enable network file sharing between different machines on your network.

Prerequisites:  
Before proceeding, ensure that you have the following:

*   An Ubuntu Server installed and properly configured.
*   Basic knowledge of Linux command-line interface (CLI).
*   Administrative access to your Ubuntu Server.

Step 1: Update the system packages:

```text-x-csrc
sudo apt update
```

```text-x-csrc
sudo apt upgrade 
```

Step 2: Install Samba:

```text-plain
sudo apt install samba
```

4.  Configure Samba:

Step 1: Create a dedicated directory for sharing files:

```text-plain
sudo mkdir /home/samba_share
```

Step 2: Configure the Samba server:  
Open the Samba configuration file using your preferred text editor:

```text-plain
sudo nano /etc/samba/smb.conf
```

Step 3: Configure a shared folder:  
At the end of the `smb.conf` file, add the following lines:

```text-plain
[SharedFolder]
comment = Samba Share
path = /home/samba_share
read only = no
browseable = yes
```

Replace `SharedFolder` with a name of your choice for the shared folder.

Step 5: Save and exit the configuration file (Ctrl+O, Ctrl+X in nano).

Step 6: Restart the Samba service for the changes to take effect:

```text-plain
sudo service smbd restart 
```

5.  Accessing the Samba Share:  
    To access the Samba share from other machines on your network, follow these steps:

Step 1: From a Windows machine:

*   Open File Explorer and enter the following in the address bar: `\\<IP_ADDRESS_OF_UBUNTU_SERVER>`
*   You should see the shared folder. Double-click to access it and provide the credentials if prompted.

Step 2: From a Linux machine:

*   Open the file manager and enter the following in the address bar: `smb://<IP_ADDRESS_OF_UBUNTU_SERVER>`
*   You should see the shared folder. Double-click to access it and provide the credentials if prompted.

Additional Samba Configuration:  
There are many additional configuration options available for Samba, such as user access control, printer sharing, and more. To explore these options, refer to the official Samba documentation: [https://www.samba.org/](https://www.samba.org/)

Conclusion:  
Congratulations! You have successfully set up a Samba server on your Ubuntu Server for network file sharing. You can now securely share files between different machines in your home lab environment. Remember to regularly update and maintain the security of your Samba server to ensure the integrity and confidentiality of your shared data.