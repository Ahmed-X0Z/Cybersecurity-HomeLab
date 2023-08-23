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

![](Images/pfsense/Screenshot%20from%202023-08-23%2007-)<img src="Images/pfsense/Screenshot%20from%202023-08-23%2007-" width="50%"/>

*   Click on **Add Network** and select **Host-only** then click **add.**
*   Do the previous step one more time.
*   Now as we add 2 more networks copy this setting for the **first** new network.

![](Images/pfsense/1_Screenshot%20from%202023-08-23%2007-)

*   And this settings for the second one.

![](Images/pfsense/2_Screenshot%20from%202023-08-23%2007-)

*   Click **save**.
*   Now let's create the virtual machine, click on **Create a New Virtual Machine**.

![](Images/pfsense/Screenshot%20from%202023-08-21%2020-)

*   choose **Typical (recommended)**.
    *   click **next**.

![](Images/pfsense/1_Screenshot%20from%202023-08-21%2020-)

*   Select Use **ISO image** and click **Browse** and open pfsense ISO file that we decompressed previously.
    *   click next.

![](Images/pfsense/Screenshot%20from%202023-08-23%2008-)

*   Change the **Virtual Machine Name** as you want.
    *   click next

![](Images/pfsense/1_Screenshot%20from%202023-08-23%2008-)

*   For the Disk Size leave it as default
    *   click next.

![](Images/pfsense/2_Screenshot%20from%202023-08-23%2008-)

*   Click **Customize Hardware**.

![](Images/pfsense/3_Screenshot%20from%202023-08-23%2008-)

*   Change the **Memory** size to **2GB**.

![](Images/pfsense/4_Screenshot%20from%202023-08-23%2008-)

*   click **add**.
    *   choose Network Adapter.
    *   click finish.
*   Add 2 more network adapters.

![](Images/pfsense/5_Screenshot%20from%202023-08-23%2008-)

*   change the new adapters _VMnet interface as shown below._
    *   _click close._

![](Images/pfsense/6_Screenshot%20from%202023-08-23%2008-)

*   Run the Virtual Machine.
    *   the machine will start with this screen stick with default settings except the **partitioning** choose **Auto (UFS)**.

![](Images/pfsense/Screenshot%20from%202023-08-21%2021-)

![](Images/pfsense/1_Screenshot%20from%202023-08-21%2021-)

*   After finishing the installation process, you should end up with this screen.

![](Images/pfsense/2_Screenshot%20from%202023-08-21%2021-)

**Configuration**

*   Select option number **2 Set interface(s) IP address**.

![](Images/pfsense/Screenshot%20from%202023-08-23%2014-)

*   Select the second interface **(LAN)**.

![](Images/pfsense/1_Screenshot%20from%202023-08-23%2014-)

*   Type **n,** and press enter.

![](Images/pfsense/2_Screenshot%20from%202023-08-23%2014-)

*   Give the interface a valid IP in your main network the default is 192.168.1.0/24.

![](Images/pfsense/3_Screenshot%20from%202023-08-23%2014-)

*    Enter your main network subnet mask the default is **24**.
*   For the rest of the options use the configuration below.

![](Images/pfsense/4_Screenshot%20from%202023-08-23%2014-)

Now you can access the pfsense web interface by opening [**https://192.168.1.200**](https://192.168.1.200) in the browser and continue configuring it.
