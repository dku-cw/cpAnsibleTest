# cpAnsibleTest

Repository for testing Ansible in combination with Check Point appliances.

#### Ansible Server
> https://github.com/jimoq/cpAnsibleDemo
```
cd ~
sudo apt-add-repository -y ppa:ansible/ansible
sudo apt-get update
sudo apt-get install -y ansible python-pip mtools unzip
pip install netaddr

cd ~
git clone --recursive https://github.com/CheckPointSW/cpAnsible
sudo cp -r cpAnsible/check_point_mgmt/ /usr/lib/python2.7/dist-packages/ansible/
```

> https://github.com/CheckPointSW/cp_mgmt_api_python_sdk
```
pip install git+https://github.com/CheckPointSW/cp_mgmt_api_python_sdk

mkdir -p $HOME/.ansible/plugins/modules
cp -r cpAnsible/check_point_mgmt/ $HOME/.ansible/plugins/modules/
```


```
/etc/ansible/hosts

[gateway:vars]
ansible_user=ApplianceUser
ansible_ssh_pass=AppliancePassword
ansible_python_interpreter=/usr/bin/python

[gateway]
192.168.121.2

[management:vars]
ansible_user=ApplianceUser
ansible_ssh_pass=AppliancePassword
ansible_python_interpreter=/usr/bin/python

[management]
192.168.121.3
```


```
/etc/ansible/ansible.cfg

library = /usr/share/ansible
mkdir /usr/share/ansible
mkdir /usr/share/ansible/check_point_mgmt
cp /mnt/hgfs/VM_Share/cpAnsible-master/check_point_mgmt/* /usr/share/ansible/check_point_mgmt
```

###### H6 VM creation Gateway
    * "Custom" Settings
    * Highest hardware compatibility available
    * "I will install the operating system later"
    * Linux - Red Hat Enterprise Linux 7 64-bit (highest version)
    * R80-20_GW for Gateway, R80-20_MGMT for Management
    * 4 GB RAM
    * 1 CPU, 2 Cores
    * VMnet1
    * LSI Logic SAS
    * SCSI
    * [x] "Store virtual disk as a single file"
    * 100 GB SAS HDD
    * ISO file pointing to Gateway ISO
    * 7 Network adapters, first VMnet1 (Host only), second VMnet2, ...
    * USB Controller with option Share Bluetooth devices with the virtual machine disabled
    * Display on default settings
    * Audio / Printer removed

###### H6 Gateway initial installation
    * 8 GB Swap, 15 GB System Root, 50 GB Logs, 26 GB Backup and Upgrade
    * Management on eth0
    * IP 192.168.121.2
    * Subnet 255.255.255.0
    * GW 192.168.121.254




###### H6 VM creation Management
    * "Custom" Settings
    * Highest hardware compatibility available
    * "I will install the operating system later"
    * Linux - Red Hat Enterprise Linux 7 64-bit (highest version)
    * R80-20_GW for Gateway, R80-20_MGMT for Management
    * 4 GB RAM
    * 1 CPU, 2 Cores
    * VMnet1
    * LSI Logic SAS
    * SCSI
    * [x] "Store virtual disk as a single file"
    * 100 GB SAS HDD
    * ISO file pointing to Gateway ISO
    * USB Controller with option Share Bluetooth devices with the virtual machine disabled
    * Display on default settings
    * Audio / Printer removed


* Management initial installation
    * 8 GB Swap, 15 GB System Root, 50 GB Logs, 26 GB Backup and Upgrade
    * Management on eth0
    * IP 192.168.121.3
    * Subnet 255.255.255.0
    * GW 192.168.121.254







