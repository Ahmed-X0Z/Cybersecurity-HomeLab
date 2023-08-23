# Open VPN
#### **Installing Ovpn-as**

*   open a shell as a root.

```text-plain
sudo su
```

*   Install ca-certificates: This package contains the public key certificates that are used to verify the authenticity of SSL/TLS connections.

```text-plain
apt update && apt -y install ca-certificates wget net-tools gnupg
```

*   Add the OpenVPN server to your repository list. 

```text-plain
wget https://as-repository.openvpn.net/as-repo-public.asc -qO /etc/apt/trusted.gpg.d/as-repository.asc
```

```text-plain
echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/as-repository.asc] http://as-repository.openvpn.net/as/debian jammy main">/etc/apt/sources.list.d/openvpn-as-repo.list
```

*   Finally, install the OpenVPN access server.

```text-plain
apt update && apt -y install openvpn-as
```

**If you faced the following error**
![](Images/Open%20VPN/image.png)

Try:

```text-plain
apt --fix-broken install
```

* * *

After installation is complete you should see something like this.

![](Images/Open%20VPN/1_image.png)

Now copy the **Admin UI** link and access it through your browser, it will open a login portal that looks like that: 

![](Images/sOpen%20VPN/2_image.png)

You can enter the credentials provided after the installation to login and start configuring your vpn server.
