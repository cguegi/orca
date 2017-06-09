# Overview
This set of playbooks can be used to deploy an Ambari-managed Hadoop cluster (HDP 2.6) containing Spark services using Ansible. These playbooks target CentOS 7.x operating systems.

## Prerequisites
The following tools are required to run these scripts:

- [Git](https://git-scm.com/)
- [Ansible](http://www.ansible.com/) (2.2.2.1 or 2.2.2.0)
- [Vagrant](https://www.vagrantup.com/) (1.9.4+)
- Install the Hostmanager plugin for vagrant - Run `vagrant plugin install vagrant-hostmanager` on the machine where Vagrant is
installed
- [Virtualbox](https://virtualbox.org) 5.0.16

### Ensure vagrant hostmanager is installed

To check and make sure you have the plugin installed execute the following:

 ```
 vagrant plugin list
 ```

If you have it installed you should see the following listed in the output:

  ```
  vagrant-hostmanager (1.8.1)
  ```
If it is not installed, you can install it with the following command:

  ```
  vagrant plugin install vagrant-hostmanager
  ```
### Nodes
```
192.168.50.3 ambari.localdomain
192.168.50.4 master1.localdomain
192.168.50.5 master2.localdomain
192.168.50.6 slave1.localdomain
192.168.50.7 slave2.localdomain
192.168.50.8 slave3.localdomain
```

## Ambari
Open the ambari web interface on http://ambari.localdomain:8080 (admin/admin)
