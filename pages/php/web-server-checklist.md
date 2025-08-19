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


## Install Net-Tools (Network Utilities)

Run the following command in your terminal:

```bash
sudo apt install net-tools
```

<div class="checklist localstore">

- [ ] Net-tools installed

</div>


## Install Apache (Web Server)

Run the following command in your terminal:

```bash
sudo apt-get install apache2
```

<div class="checklist localstore">

- [ ] Apache installed

</div>


## Install PHP (Programming Language)

Run the following command in your terminal:

```bash
sudo apt-get install php
```

<div class="checklist localstore">

- [ ] PHP installed

</div>


## Install MySQL (Database Server)

Run the following command in your terminal:

```bash
sudo apt-get install mysql-server
```

<div class="checklist localstore">

- [ ] MySQL installed

</div>


## Install PHP-MySQL Drivers

Run the following command in your terminal:

```bash
sudo apt-get install php-mysql
```

<div class="checklist localstore">

- [ ] PHP-MySQL drivers installed

</div>


## Install OpenSSH Server

Run the following command in your terminal:

```bash
sudo apt-get install openssh-server
```

<div class="checklist localstore">

- [ ] OpenSSH Server installed

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

Run the following commands in your terminal:

```bash
sudo useradd devuser
sudo passwd devuser
```

When prompted, type the password:

```
dev123
```

> [!IMPORTANT] You will NOT see the characters as you type.

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

Then, scroll to the bottom (approximately line 124) and add:

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

Run the following command in your terminal:

```bash
sudo chmod 777 /var/www/html
```

<div class="checklist localstore">

- [ ] `devuser` has access to the web root

</div>


## Restart SSH Service

```bash
sudo service ssh restart
```

<div class="checklist localstore">

- [ ] SSH Service restarted

</div>
