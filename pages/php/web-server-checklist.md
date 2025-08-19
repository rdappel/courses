---
title: PHP Web Server Setup
subtitle: PHP
hideNav: false

live: https://fvtc.software/appel/php/testing
dev: http://localhost:3006/appel/php/testing
repo: https://github.com/rdappel/courses
---

# Web Server Checklist { #web-server-checklist }

Running the following commands on your Web Server will set up a basic PHP environment. These 

> [!NOTE] This checklist will save to local storage (this computer).


## Update the Apt package list { #update-apt-packages }

Run the following command in your terminal:

```bash
sudo apt update
```

<div class="checklist localstore">
- [ ] Apt package list updated
</div>


## Install Apache, PHP, MySQL, and related tools { #install-apache-php-mysql }

Run the following command in your terminal:

```bash
sudo apt install apache2 php mysql-server php-mysql net-tools openssh-server
```

- [ ] Apache, PHP, MySQL, and related tools installed


## Backup SSH Config File

Run the following command in your terminal:

```bash
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

- [ ] SSH Config File backed up


## Add a New SFTP Group

Run the following command in your terminal:

```bash
sudo groupadd sftponly
```

- [ ] SFTP Group added


## Add a New User

Run the following command in your terminal:

> [!IMPORTANT] Remember to use password `dev123` when prompted.

```bash
sudo adduser devuser
```

- [ ] New user created


## Add User to SFTP Group

Run the following command in your terminal:

```bash
sudo usermod -a -G sftponly devuser
```

- [ ] `devuser` added to the SFTP Group


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
- [ ] Updated the SSH Config File

## Set Permissions for the Web Root { #set-web-root-permissions }

Run the following commands in your terminal:

```bash
sudo chown devuser:sftponly /var/www/html
```

```bash
sudo chmod 775 /var/www/html
```

- [ ] `devuser` has access to the web root

## Restart SSH Service

```bash
sudo systemctl restart ssh
```

- [ ] SSH Service restarted

</div>