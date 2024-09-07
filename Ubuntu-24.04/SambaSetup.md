# Samba Setup

## Install Sanba

```code
sudo apt update && sudo apt install -y samba
```

## Directory to share files from

```code
mkdir ~/sambashare
```

## Config Samba

```code
sudo nano /etc/samba/smb.conf
```

### Edit /etc/samba/smb.conf

```txt
[global]

### Browsing/Identification ###

# Change this to the workgroup/NT-domain name Samba server will part of
   workgroup = WORKGROUP
   server min protocol = NT1
```

```txt
[sambashare]
   comment = A Samba share on Ubuntu 24.04LTS
   path = /home/<userneme>/sambashare
   read only = no
   browsable = yes
```

* Save and Exit nano
  * To Save: [Ctrl]+[o]
  * To Exit: [Ctrl]+[w]

### Set Samba password

```code
sudo smbpasswd -a <username>
```

### Restart Samba

```code
sudo service smbd restart
```
