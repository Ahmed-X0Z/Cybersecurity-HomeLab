# Ubuntu installation
**Step 1: Download Ubuntu ISO**

1.  Visit the official Ubuntu website ([https://ubuntu.com/](https://ubuntu.com/)) or the Ubuntu download page ([https://ubuntu.com/download](https://ubuntu.com/download)).
2.  Choose the Ubuntu version you want to install (e.g., Ubuntu 20.04 LTS) and click on the download link to obtain the ISO file.

**Step 2: Create a Bootable USB Drive**

1.  Insert a USB flash drive (8GB or larger) into your computer.
2.  Download and install a tool like Rufus (for Windows) or Etcher (for macOS and Linux) to create a bootable USB drive.
3.  Open the tool and select the downloaded Ubuntu ISO file.
4.  Choose the USB drive you inserted as the destination for creating the bootable drive.
5.  Start the process and wait for the tool to finish creating the bootable USB drive.

**Step 3: Installing Ubuntu**

1.  The computer will now boot from the USB drive and display the Ubuntu installer.
2.  Select your language and click "Install Ubuntu."
3.  Choose your keyboard layout and click "Continue."
4.  On the "Updates and Other Software" screen, choose the Minimal installation.
5.  On the "Installation Type" screen, choose the "Erase disk and install Ubuntu" option. Alternatively, you can choose the "Something else" option for manual partitioning.
6.  Follow the on-screen instructions to set up your location, keyboard layout, and user account details.
7.  Click "Install" to begin the installation process.
8.  The installer will copy files, install packages, and configure the system. This may take some time.
9.  Once the installation is complete, you'll be prompted to restart your computer. Remove the USB drive before restarting.

**Step 4: Post-Installation Setup**

1.  Open Network Settings
    1.  Click on the network icon in the top-right corner of the Ubuntu desktop.
    2.  Select "Wi-Fi Settings" or "Wired Settings" based on your network connection.
2.  Access Network Connection Properties
    1.  In the network settings window, locate your network connection (Wi-Fi or Ethernet) and click on the gear icon next to it to access the connection properties.
3.  Configure IPv4 Settings
    1.  In the connection properties window, select the "IPv4" tab.
    2.  From the "Method" dropdown menu, select "Manual" to specify a static IP address.
    3.  Click on the "Add" button to add the static IP configuration.
4.  Enter IP Address Details
    1.  In the "Addresses" field, enter the desired static IP address. For example, `192.168.1.100`.
    2.  In the "Netmask" field, enter the subnet mask. For example, `255.255.255.0`.
    3.  In the "Gateway" field, enter the IP address of your network gateway. For example, `192.168.1.1`.
    4.  In the "DNS servers" field, enter the IP addresses of the DNS servers you want to use, separated by commas or you can leave it automatic.
5.  Save and Apply Changes
    1.  Click on the "Apply" button to save the changes and apply the static IP configuration.
    2.  Close the network settings window.