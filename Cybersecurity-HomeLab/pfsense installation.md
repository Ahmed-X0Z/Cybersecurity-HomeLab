# pfsense installation
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

![](Images/pfsense%20installation/Screenshot%20from%202023-08-23%2007.png)

*   Click on **Add Network** and select **Host-only** then click **add.**
*   Do the previous step one more time.
*   Now as we add 2 more networks copy this setting for the **first** new network.

![](Images/pfsense%20installation/1_Screenshot%20from%202023-08-23%2007.png)

*   And this settings for the second one.

![](Images/pfsense%20installation/2_Screenshot%20from%202023-08-23%2007.png)

*   Click **save**.
*   Now let's create the virtual machine, click on **Create a New Virtual Machine**.

![](Images/pfsense%20installation/Screenshot%20from%202023-08-21%2020.png)

*   choose **Typical (recommended)**.
    *   click **next**.

![](Images/pfsense%20installation/1_Screenshot%20from%202023-08-21%2020.png)

*   Select Use **ISO image** and click **Browse** and open pfsense ISO file that we decompressed previously.
    *   click next.

![](Images/pfsense%20installation/Screenshot%20from%202023-08-23%2008.png)

*   Change the **Virtual Machine Name** as you want.
    *   click next

![](Images/pfsense%20installation/1_Screenshot%20from%202023-08-23%2008.png)

*   For the Disk Size leave it as default
    *   click next.

![](Images/pfsense%20installation/2_Screenshot%20from%202023-08-23%2008.png)

*   Click **Customize Hardware**.

![](Images/pfsense%20installation/3_Screenshot%20from%202023-08-23%2008.png)

*   Change the **Memory** size to **2GB**.

![](Images/pfsense%20installation/4_Screenshot%20from%202023-08-23%2008.png)

*   click **add**.
    *   choose Network Adapter.
    *   click finish.
*   Add 2 more network adapters.

![](Images/pfsense%20installation/5_Screenshot%20from%202023-08-23%2008.png)

*   change the new adapters _VMnet interface as shown below._
    *   _click close._

![](Images/pfsense%20installation/6_Screenshot%20from%202023-08-23%2008.png)

*   Run the Virtual Machine.
    *   the machine will start with this screen stick with default settings except the **partitioning** choose **Auto (UFS)**.

![](Images/pfsense%20installation/Screenshot%20from%202023-08-21%2021.png)

![](Images/pfsense%20installation/1_Screenshot%20from%202023-08-21%2021.png)

*   After finishing the installation process, you should end up with this screen.

![](Images/pfsense%20installation/2_Screenshot%20from%202023-08-21%2021.png)

**Configuration**

*   Select option number **2 Set interface(s) IP address**.

![](Images/pfsense%20installation/Screenshot%20from%202023-08-23%2014.png)

*   Select the second interface **(LAN)**.

![](Images/pfsense%20installation/1_Screenshot%20from%202023-08-23%2014.png)

*   Type **n,** and press enter.

![](Images/pfsense%20installation/2_Screenshot%20from%202023-08-23%2014.png)

*   Give the interface a valid IP in your main network the default is 192.168.1.0/24.

![](Images/pfsense%20installation/3_Screenshot%20from%202023-08-23%2014.png)

*    Enter your main network subnet mask the default is **24**.
*   For the rest of the options use the configuration below.

![](Images/pfsense%20installation/4_Screenshot%20from%202023-08-23%2014.png)

Now you can access the pfsense web interface by opening [**https://192.168.1.200**](https://192.168.1.200) in the browser and continue configuring it.