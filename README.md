# ansible-role-ubuntu_autoinstall

This role will:
* Download and verify (GPG and SHA256) the newest Ubuntu Server 20.04 ISO
* Unpack the ISO and integrates the user-data file for semi-automated installation
* Repack the ISO and (optionally) uploads it to [PiKVM](https://pikvm.org/) for futher installation

Special thanks to:
* covertsh for [Ubuntu Autoinstall Generator](https://github.com/covertsh/ubuntu-autoinstall-generator) – this repo is pretty much an Ansible version of his script
