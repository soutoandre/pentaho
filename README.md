#  Pentaho

## Introduction

Installation Pentaho Data Integration

### To install Pentaho run the following command below

sudo ansible-playbook site.yml  -e " host=pentaho installpentaho=True"  --limit pentaho.example.com

## Requirements

1. to disable  selinux e firewalld

SELinux

```
sed -i 's/enforcing/disabled/g' /etc/selinux/config /etc/selinux/config
reboot


Firewall

systemctl mask firewalld
systemctl stop firewalld



2.  Before of run the playbook of instalation, Have to create Logical Volume.


## Sistema Operacional CentOS 7
 
## Create  Volume Group **VG00**

# Create partitioning  Disk
fdisk /dev/sdc

# Create Volume Group
vgcreate VG01  /dev/sdc1

# Display  VG00
vgdisplay -v VG00

# Create  Logical Volume
lvcreate -l100%FREE -n lvol00 VG00

# Display Logical Volume
lvdisplay -v lvol00

# Create filesystem
mkfs.xfs  -L PENTAHO /dev/VG00/lvol00

# Create directory
mkdir /pentaho

## Edit  /etc/fstab and include line below
vi /etc/fstab

LABEL=PENTAHO   /pentaho             xfs    defaults        1 2


## Mount filesystem

mount -av


