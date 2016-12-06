JUNOS Automation Learning Environment
=====================================
This repository contains the files required to build
a small test environment for learning and testing 
automation tools with JUNOS.

Two environments are included: 
 - simple: One vSRX and one Ubuntu VM
 - east_west: Two Ubuntu VMs connected to different interfaces
              on the vSRX

The ubuntu VMs are preconfigured with the following packages:
 - Python2 and Python3
 - PyEZ 2 (junos-eznc)
 - Ansible 2

Software Requirements
---------------------
The environments use VirtualBox, a free, mulit-platform hypervisor
to host the Ubuntu and vSRX VMs.  VirtualBox 5.1.8 or newer is
recommended. VirtualBox can be downloaded from https://www.virtualbox.org/wiki/Downloads

The setup and configurations of the VMs is automated using Vagrant.
Download Vagrant for your platform from https://www.vagrantup.com/downloads.html

Although optional, git is highly recommended.  Download git from https://git-scm.com

Setup
-----
The setup of the environment, including the download of the vSRX and Ubuntu 
VM images, is automated.  

Use git clone to download the repository:
```
git clone https://github.com/cbinckly/junos-automation-environment.git
```

Once the repository is downloaded you can provision either environment by
changing into the directory and bringing it up with Vagrant.

For the simple environment:
```
cd simple/
vagrant up
```

For the east_west environment:
```
cd simple/
vagrant up
```

To connect to the vms in the environment, use vagrant ssh:
```
vagrant ssh ubuntu
vagrant ssh ubuntu_east
vagrant ssh ubuntu_west
vagrant ssh vsrx
```

Environments
------------

Simple
```
+------------+                   +------------+
| Ubuntu VM  |___________________|   vSRX     |
| 172.16.0.3 | eth1     ge-0/0/1 | 172.16.0.2 |
+------------+                   +------------+
```

East West
```
                                 +------------+                   +------------+
+------------+                   | 172.16.0.2 |___________________| 172.16.0.3 |
| Ubuntu West|___________________|   vSRX     | ge-0/0/1     eth1 | Ubuntu East|
| 172.17.0.3 | eth1     ge-0/0/2 | 172.17.0.2 |                   +------------+
+------------+                   +------------+
```

