# Ansible Role: Ubuntu Autoinstall

### This role will:
* Download and verify (GPG and SHA256) the newest Ubuntu Server 20.04 ISO
* Unpack the ISO and integrate the user-data file for semi-automated installation
* Repack the ISO and (optionally) upload it to [PiKVM](https://pikvm.org/) for futher installation

### Special thanks to:
* covertsh for [Ubuntu Autoinstall Generator](https://github.com/covertsh/ubuntu-autoinstall-generator) – this repo is pretty much an Ansible version of their script


### Example playbook:
```
---
- hosts: all
  gather_facts: yes
  become: yes

  roles:
    - role: notthebee.ubuntu_autoinstall
```

### Example inventory:
```
[target]
target ansible_host=192.168.1.2 ansible_user=foo ansible_connection=ssh ansible_ssh_private_key_file=/Users/foo/.ssh/id_rsa


[pikvm]
pikvm ansible_host=192.168.1.3 ansible_user=root ansible_connection=ssh
```

### Variables
**boot_drive_serial** – the serial number of the drive where you want to install Ubuntu. You can find it out using `ls /dev/disk/by-id`. Make sure to omit the interface (e.g. **ata-** or **scsi-**).

You can also use **/dev/sd*** to point the installer to the boot drive, but please, for the love of God, **do not** do that on a production server. The installer will **wipe the drive** specified in this playbook without confirmation or remorse.

Other variables are more or less self-explanatory and can be found in defaults/main.yml