---
id: 006-sftp-setup
title: SFTP Configuration in Linux(CENTOS)
tags: 
    - sftp
    - ftp
    - centos
    - linux
date: 2021-10-01 16:53:39 +0530
keywords: sftp, ftp, linux, centos
categories: linux
cover:
author: Subhendu Gogoi
meta-description: SFTP Setup in Linux(CENTOS)
---

# SFTP Configuration

## What is SFTP?

SFTP (Secure File Transfer Protocol) is a file transfer protocol that leverages a set of utilities that provide secure access to a remote computer to deliver secure communications. It leverages SSH (Secure Socket Shell or Secure Shell) and is frequently also referred to as 'Secure Shell File Transfer Protocol'.

## Instructions

To install an SFTP server on a CENTOS Linux Server, follow the below steps:
1. Execute the following command to check whether SSH is installed
```
    sudo rpm -qa | grep ssh
```

2. If SSH is not installed, run the following command
```
    sudo yum install openssh-server
```

3. Open port 22
```
    sudo iptables -I INPUT -p tcp --dport 22 -j ACCEPT
```

4. Create a user and provide new password for that user
```
    sudo useradd {user_name}
    sudo passwd {user_name}
```

5. Create a directory for the file transfer and make the changes
```
    sudo mkdir {directory_name}
    sudo chgrp {user_name} {directory_name}
    sudo chown {user_name} {directory_name}
```

6. In /etc/ssh/sshd_config file add the below configuration:
```
    Match User {user_name}
    ForceCommand internal-sftp
    PubkeyAuthentication yes
    PasswordAuthentication yes
    ChrootDirectory {directory_name}
    PermitTunnel no
    AllowAgentForwarding no
    AllowTcpForwarding no
    X11Forwarding no
```

7. Restart the SFTP Service
```
    sudo systemctl restart sshd.service
```

8. Testing(provide password on prompted)
```
    sftp {user_name}@{server_address}
```
