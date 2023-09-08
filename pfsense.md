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

<img src="Images/pfsense/Screenshot%20from%202023-08-23%2007-" width="60%"/>

*   Click on **Add Network** and select **Host-only** then click **add.**
*   Do the previous step one more time.
*   Now as we add 2 more networks copy this setting for the **first** new network.

<img src="Images/pfsense/1_Screenshot%20from%202023-08-23%2007-" width="60%"/>

*   And this settings for the second one.

<img src="Images/pfsense/2_Screenshot%20from%202023-08-23%2007-" width="60%"/>

*   Click **save**.
*   Now let's create the virtual machine, click on **Create a New Virtual Machine**.

<img src="Images/pfsense/Screenshot%20from%202023-08-21%2020-" width="60%"/>

*   choose **Typical (recommended)**.
    *   click **next**.

<img src="Images/pfsense/1_Screenshot%20from%202023-08-21%2020-" width="60%"/>

*   Select Use **ISO image** and click **Browse** and open pfsense ISO file that we decompressed previously.
    *   click next.

<img src="Images/pfsense/Screenshot%20from%202023-08-23%2008-" width="60%"/>

*   Change the **Virtual Machine Name** as you want.
    *   click next

<img src="Images/pfsense/1_Screenshot%20from%202023-08-23%2008-" width="60%"/>

*   For the Disk Size leave it as default
    *   click next.

<img src="Images/pfsense/2_Screenshot%20from%202023-08-23%2008-" width="60%"/>

*   Click **Customize Hardware**.

<img src="Images/pfsense/3_Screenshot%20from%202023-08-23%2008-" width="60%"/>

*   Change the **Memory** size to **2GB**.

<img src="Images/pfsense/4_Screenshot%20from%202023-08-23%2008-" width="60%"/>

*   click **add**.
    *   choose Network Adapter.
    *   click finish.
*   Add 2 more network adapters.

<img src="Images/pfsense/5_Screenshot%20from%202023-08-23%2008-" width="60%"/>

*   change the new adapters _VMnet interface as shown below._
    *   _click close._

<img src="Images/pfsense/6_Screenshot%20from%202023-08-23%2008-" width="60%"/>

*   Run the Virtual Machine.
    *   the machine will start with this screen stick with default settings except the **partitioning** choose **Auto (UFS)**.

<img src="Images/pfsense/Screenshot%20from%202023-08-21%2021-" width="60%"/>

<img src="Images/pfsense/1_Screenshot%20from%202023-08-21%2021-" width="60%"/>

*   After finishing the installation process, you should end up with this screen.

<img src="Images/pfsense/2_Screenshot%20from%202023-08-21%2021-" width="60%"/>

**Configuration**

*   Select option number **2 Set interface(s) IP address**.

<img src="Images/pfsense/Screenshot%20from%202023-08-23%2014-" width="60%"/>

*   Select the second interface **(LAN)**.

<img src="Images/pfsense/1_Screenshot%20from%202023-08-23%2014-" width="60%"/>

*   Type **n,** and press enter.

<img src="Images/pfsense/2_Screenshot%20from%202023-08-23%2014-" width="60%"/>

*   Give the interface a valid IP in your main network the default is 192.168.1.0/24.

<img src="Images/pfsense/3_Screenshot%20from%202023-08-23%2014-" width="60%"/>

*    Enter your main network subnet mask the default is **24**.
*   For the rest of the options use the configuration below.

<img src="Images/pfsense/4_Screenshot%20from%202023-08-23%2014-" width="60%"/>

Now you can access the pfsense web interface by opening [**https://192.168.1.200**](https://192.168.1.200) in the browser and continue configuring it.
