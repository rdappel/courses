---
title: PHP Web Server Setup
subtitle: PHP
hideNav: false

live: https://fvtc.software/appel/php/testing
dev: http://localhost:3006/appel/php/testing
repo: https://github.com/rdappel/courses
---

# Web Server Checklist {#web-server-checklist}

Running the following commands on your Web Server will set up a basic PHP environment. 

> [!NOTE] This checklist will save to local storage (this computer).

---

## Update the apt-get package list {#update-apt-packages}

Run the following command in your terminal:

```bash
sudo apt-get update
```

<div class="checklist localstore">

- [ ] Apt package list updated

</div>


## Install Apache, PHP, MySQL {#install-apache-php-mysql}

Run the following command in your terminal:

```bash
sudo apt install apache2 php mysql-server php-mysql net-tools openssh-server
```

<div class="checklist localstore">

- [ ] Apache, PHP, MySQL, and related tools installed

</div>


## Backup SSH Config File

Run the following command in your terminal:

```bash
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

<div class="checklist localstore">

- [ ] SSH Config File backed up

</div>


## Add a New SFTP Group

Run the following command in your terminal:

```bash
sudo groupadd sftponly
```

<div class="checklist localstore">

- [ ] SFTP Group added

</div>


## Add a New User

Run the following command in your terminal:

> [!IMPORTANT] Remember to use password `dev123` when prompted.

```bash
sudo adduser devuser
```

<div class="checklist localstore">

- [ ] New user created

</div>


## Add User to SFTP Group

Run the following command in your terminal:

```bash
sudo usermod -a -G sftponly devuser
```

<div class="checklist localstore">

- [ ] `devuser` added to the SFTP Group

</div>


## Update the SSH Config File

Run the following command in your terminal:

```bash
sudo gedit /etc/ssh/sshd_config
```

Then, scroll to the bottom and add:

```bash
Match Group sftponly
    ChrootDirectory /var/www
    ForceCommand internal-sftp
    AllowTcpForwarding no
    X11Forwarding no
```

<div class="checklist localstore">

- [ ] Updated the SSH Config File

</div>


## Set Permissions for the Web Root {#set-web-root-permissions}

Run the following commands in your terminal:

```bash
sudo chown devuser:sftponly /var/www/html
```

```bash
sudo chmod 775 /var/www/html
```

<div class="checklist localstore">

- [ ] `devuser` has access to the web root

</div>


## Restart SSH Service

```bash
sudo systemctl restart ssh
```

<div class="checklist localstore">

- [ ] SSH Service restarted

</div>