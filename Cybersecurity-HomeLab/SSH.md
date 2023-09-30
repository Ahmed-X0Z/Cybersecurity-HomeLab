# SSH
**Install OpenSSH Server:**  
OpenSSH Server allows you to securely connect to your Ubuntu machine remotely.

*   Update the system packages:

```text-x-csrc
sudo apt update
```

```text-x-csrc
sudo apt upgrade 
```

*   Install OpenSSH Server:

```text-x-csrc
sudo apt install openssh-server
```

*   Make sure that it's running.

```text-x-csrc
sudo systemctl status ssh
```

**Accessing your Ubuntu Server via SSH:**  
To remotely access your Ubuntu machine using SSH, you need an SSH client on your local machine (e.g., OpenSSH on Linux or macOS, PuTTY on Windows).

Open the terminal or SSH client on your local machine.

Connect to your Ubuntu Server using the following command:

```text-plain
ssh username@<IP_ADDRESS_OR_HOSTNAME>
```

Replace `username` with your Ubuntu username, `<IP_ADDRESS_OR_HOSTNAME>` with the IP address or hostname of your Ubuntu Server,