# pfsense configuration
After finishing the installation process of **pfsense** now let's start configuring the rest of the interfaces.

First you need to access the pfsense web interface throw the web browser by enteringthe interface ip address that we configuered during the installation process for me it's [https://192.168.100.236](http://192.168.100.236)

This page should show up.

![](Images/pfsense%20configuration/image.png)

The default credentials are username: **admin**, password: **pfsense**

This is the pfsense dashboard.

![](Images/pfsense%20configuration/1_image.png)

Follow these steps to configure the other two interfaces Lan2 and DMZ.

*   click on **Interfaces**

![](Images/pfsense%20configuration/image.jpg)

*   click on **Assignments**

![](Images/pfsense%20configuration/1_image.jpg)

*   This is the configurations for Lan2

![](Images/pfsense%20configuration/2_image.png)

*   This is the configurations for DMZ

![](Images/pfsense%20configuration/3_image.png)

#### Enable DHCP for **LAN2** and **DMZ**

*   Click on **Services**

![](Images/pfsense%20configuration/2_image.jpg)

*   Click on **DHCP Server**

![](Images/pfsense%20configuration/3_image.jpg)

*   Click on **LAN2**

![](Images/pfsense%20configuration/4_image.jpg)

*   Enable DHCP on LAN2 and set a range of IPs

![](Images/pfsense%20configuration/5_image.jpg)

*   Scroll down and Click **Save**
*   Now let's configure the DHCP Server for the DMZ

![](Images/pfsense%20configuration/6_image.jpg)

*   Scroll down and Click **Save**
*   Now click on this small reload icon

![](Images/pfsense%20configuration/7_image.jpg)

* * *

**Now we need to add some rules.**

*   Click on **Firewall**

![](Images/pfsense%20configuration/8_image.jpg)

*   Click on **Rules**

![](Images/pfsense%20configuration/9_image.jpg)

*   click on **LAN2**

![](Images/pfsense%20configuration/4_image.png)

By default there will be no rules for LAN2 so the firewall is blocking all its traffic. So we will add two rules.  
The first is to allow IPv4 traffic and the second is two allwo IPv6 traffic

*   Click **add**

![](Images/pfsense%20configuration/5_image.png)

*   For IPv4 copy this configuration and click **save**

![](Images/pfsense%20configuration/6_image.png)

*   For IPv6 copy this configuration and click **save**

![](Images/pfsense%20configuration/7_image.png)

*   After adding the two rules click on **Apply Changes**

![](Images/pfsense%20configuration/8_image.png)

I will test these new rules using Lubuntu system as a virtual machine you can use any distro but make sure it's attached to the Lan2 network.

For Lubuntu installation guide click [here](Lubuntu%20installation%20for%20the%20S.md)

*   Go to VMware
*   Right click on your virtual machine
*   Click on settings

![](Images/pfsense%20configuration/10_image.jpg)

*   Click on **Network Adapter** and change it to **Custom** and make sure to chose the right VMnet for LAN2

![](Images/pfsense%20configuration/Screenshot%20from%202023-09-22%2012-)

*   Click **save**
*   Now open a terminal and use `**ifconfig**` to check that the DHCP server is working correctly and the machine reserved a valid IP address.

![](Images/pfsense%20configuration/11_image.jpg)

*   Since the DHCP is working correctly now let's use the ping command and ping google to check if the rules are working correctly.

![](Images/pfsense%20configuration/12_image.jpg)

*   Now if we tried to ping the DMZ interface, we will see that we can ping it so we need to add a rule to the firewall to disallow that.

![](Images/pfsense%20configuration/13_image.jpg)

*   Open pfsense web interface once again
*   Go to **firewall rules**
*   Switch to **LAN2**
*   Copy this configuration

![](Images/pfsense%20configuration/9_image.png)

*   Click **Save**
*   Click **Apply Changes**

Now if you try to ping the DMZ interface you will find that it's not accessable.

![](Images/pfsense%20configuration/14_image.jpg)

I also added another role to block traffic from **LAN2** to **LAN** here its configuration.

![](Images/pfsense%20configuration/10_image.png)

**Now let's add some rules for the DMZ Network**

![](Images/pfsense%20configuration/18_image.png)

*   Enable ICMP (Ping) Traffic

![](Images/pfsense%20configuration/11_image.png)

*   Enable HTTPS internet access

![](Images/pfsense%20configuration/12_image.png)

*   Enable HTTP internet access

![](Images/pfsense%20configuration/13_image.png)

*   Enable DNS Traffic

![](Images/pfsense%20configuration/17_image.png)

*   Block traffic from DMZ to LAN2

![](Images/pfsense%20configuration/14_image.png)

*   Block traffic from DMZ to LAN

![](Images/pfsense%20configuration/16_image.png)

*   Block Pfsense Web config 

![](Images/pfsense%20configuration/15_image.png)

* * *