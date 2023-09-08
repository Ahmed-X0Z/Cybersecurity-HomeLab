# pfsense
pfSense is an open-source firewall and routing platform based on FreeBSD.

**Requirements**

1.  Install your favorite virtual machine hypervisor virtual machine hypervisor (VMware, VBOX), Iam using VMware-workstation, but you can use any VM Hypervisor.
2.  Download the pfsense iso image through this link: [Download pfSense Community Edition](https://www.pfsense.org/download/)
3.  Now move to the **Downloads directory** or to the directory which you downloaded the iso image.
4.  decompress the file.

```text-plain
gzip -d <filename>.gz
```

**Setup**

*   Open **VMware**.
*   Click on **Edit** on the top menu then **Virtual Network Editor**.
<p align="center">
<img src="Images/pfsense/Screenshot%20from%202023-08-23%2007-" width="60%"/>
</p>
*   Click on **Add Network** and select **Host-only** then click **add.**
*   Do the previous step one more time.
*   Now as we add 2 more networks copy this setting for the **first** new network.
<p align="center">
<img src="Images/pfsense/1_Screenshot%20from%202023-08-23%2007-" width="60%"/>
</p>
*   And this settings for the second one.
<p align="center">
<img src="Images/pfsense/2_Screenshot%20from%202023-08-23%2007-" width="60%"/>
</p>
*   Click **save**.
*   Now let's create the virtual machine, click on **Create a New Virtual Machine**.
<p align="center">
<img src="Images/pfsense/Screenshot%20from%202023-08-21%2020-" width="60%"/>
</p>
*   choose **Typical (recommended)**.
    *   click **next**.
<p align="center">
<img src="Images/pfsense/1_Screenshot%20from%202023-08-21%2020-" width="60%"/>
</p>
*   Select Use **ISO image** and click **Browse** and open pfsense ISO file that we decompressed previously.
    *   click next.
<p align="center">
<img src="Images/pfsense/Screenshot%20from%202023-08-23%2008-" width="60%"/>
</p>
*   Change the **Virtual Machine Name** as you want.
    *   click next
<p align="center">
<img src="Images/pfsense/1_Screenshot%20from%202023-08-23%2008-" width="60%"/>
</p>
*   For the Disk Size leave it as default
    *   click next.
<p align="center">
<img src="Images/pfsense/2_Screenshot%20from%202023-08-23%2008-" width="60%"/>
</p>
*   Click **Customize Hardware**.
<p align="center">
<img src="Images/pfsense/3_Screenshot%20from%202023-08-23%2008-" width="60%"/>
</p>
*   Change the **Memory** size to **2GB**.
<p align="center">
<img src="Images/pfsense/4_Screenshot%20from%202023-08-23%2008-" width="60%"/>
</p>
*   click **add**.
    *   choose Network Adapter.
    *   click finish.
*   Add 2 more network adapters.
<p align="center">
<img src="Images/pfsense/5_Screenshot%20from%202023-08-23%2008-" width="60%"/>
</p>
*   change the new adapters _VMnet interface as shown below._
    *   _click close._
<p align="center">
<img src="Images/pfsense/6_Screenshot%20from%202023-08-23%2008-" width="60%"/>
</p>
*   Run the Virtual Machine.
    *   the machine will start with this screen stick with default settings except the **partitioning** choose **Auto (UFS)**.
<p align="center">
<img src="Images/pfsense/Screenshot%20from%202023-08-21%2021-" width="60%"/>

<img src="Images/pfsense/1_Screenshot%20from%202023-08-21%2021-" width="60%"/>
</p>
*   After finishing the installation process, you should end up with this screen.
<p align="center">
<img src="Images/pfsense/2_Screenshot%20from%202023-08-21%2021-" width="60%"/>
</p>
**Configuration**

*   Select option number **2 Set interface(s) IP address**.
<p align="center">
<img src="Images/pfsense/Screenshot%20from%202023-08-23%2014-" width="60%"/>
</p>
*   Select the second interface **(LAN)**.
<p align="center">
<img src="Images/pfsense/1_Screenshot%20from%202023-08-23%2014-" width="60%"/>
</p>
*   Type **n,** and press enter.
<p align="center">
<img src="Images/pfsense/2_Screenshot%20from%202023-08-23%2014-" width="60%"/>
</p>
*   Give the interface a valid IP in your main network the default is 192.168.1.0/24.
<p align="center">
<img src="Images/pfsense/3_Screenshot%20from%202023-08-23%2014-" width="60%"/>
</p>
*    Enter your main network subnet mask the default is **24**.
*   For the rest of the options use the configuration below.
<p align="center">
<img src="Images/pfsense/4_Screenshot%20from%202023-08-23%2014-" width="60%"/>
</p>
Now you can access the pfsense web interface by opening [**https://192.168.1.200**](https://192.168.1.200) in the browser and continue configuring it.
