# Remote Desktop
For remote desktop connection I will use **Xrdp**.

**Xrdp** is an open-source implementation of the Microsoft Remote Desktop Protocol (RDP) that allows you to graphically control a remote system.

*   **Update the system packages:**

```text-x-csrc
sudo apt update
```

```text-plain
sudo apt upgrade
```

### **Installing Xrdp**

```text-plain
sudo apt install xrdp 
```

Once the installation is complete, the Xrdp service will automatically start. You can verify it by typing:

```text-plain
sudo systemctl status xrdp
```

By default Xrdp uses the `/etc/ssl/private/ssl-cert-snakeoil.key` file that is readable only by members of the “ssl-cert” group. Run the following command to add the `xrdp` user to the group:

```text-plain
sudo adduser xrdp ssl-cert 
```

Restart the Xrdp service for changes to take effect:

```text-plain
sudo systemctl restart xrdp
```

The Xrdp daemon listens on port `3389` on all interfaces. If you run a firewall on your Ubuntu server , you’ll need to open the Xrdp port.

To allow access to the Xrdp server from a specific IP address or IP range, for example, `192.168.1.0/24`, you would run the following command:

```text-plain
sudo ufw allow from 192.168.1.0/24 to any port 3389
```

If you want to allow access from anywhere (which is highly discouraged for security reasons), run:

```text-plain
sudo ufw allow 3389
```

Now you can access the server through any rdp client using your server Ip address.