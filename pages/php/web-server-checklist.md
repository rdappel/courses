---
title: PHP Web Server Setup
subtitle: PHP
hideNav: false

live: https://fvtc.software/appel/php/testing
dev: http://localhost:3006/appel/php/testing
repo: https://github.com/rdappel/courses
---

# Web Server Checklist

Running the following commands on your Web Server will set up a basic PHP environment. These 

> [!NOTE] This checklist will save to local storage (this computer).

<div class="checklist localstore">


1. [ ] Update package list

```bash
sudo apt update
```

2. [ ] Install Apache, PHP, MySQL, and related tools

```bash
sudo apt install apache2 php mysql-server php-mysql net-tools openssh-server
```

- [ ] Backup SSH Config File

```bash
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

- [ ] Add a New SFTP Group

```bash
sudo groupadd sftponly
```

- [ ] Add a New User (Remember to use password: `dev123`)

```bash
sudo adduser devuser
```

- [ ] Add devuser to the SFTP Group

```bash
sudo usermod -a -G sftponly devuser
```

- [ ] Update the SSH Config File

```bash
sudo nano /etc/ssh/sshd_config
```

- [ ] Scroll to the bottom and add:

```bash
Match Group sftponly
    ChrootDirectory /var/www
    ForceCommand internal-sftp
    AllowTcpForwarding no
    X11Forwarding no
```

- [ ] Give devuser access to the web root

```bash
sudo chown devuser:sftponly /var/www/html
```

```bash
sudo chmod 775 /var/www/html
```

- [ ] Restart SSH Service
```bash
sudo systemctl restart ssh
```

</div>