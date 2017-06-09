# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  #config.vm.box = "puppetlabs/centos-6.6-64-nocm"
  #config.vm.box = "puppetlabs/centos-7.0-64-nocm"
  config.vm.box = "centos/7"
  config.vm.box_check_update = false
  config.ssh.insert_key = true
  
  # enable the hostmanager plugin
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.manage_guest = true
  
 
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", 1280 ]
    vb.customize ["modifyvm", :id, "--cpus", 1 ]
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
    
    # enable promisc mode on the network interface
    vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
  end

  config.vm.define "ambari" do |ambari|
    ambari.vm.network "private_network", ip: "192.168.50.3"
    ambari.vm.hostname = "ambari.localdomain"
  end
  
  config.vm.define "master1" do |master1|
    master1.vm.network "private_network", ip: "192.168.50.4"
    master1.vm.hostname = "master1.localdomain"
  end
  
  config.vm.define "master2" do |master2|
    master2.vm.network "private_network", ip: "192.168.50.5"
    master2.vm.hostname = "master2.localdomain"

  end
  
  config.vm.define "slave1" do |slave1|
    slave1.vm.network "private_network", ip: "192.168.50.6"
    slave1.vm.hostname = "slave1.localdomain"
  end

  config.vm.define "slave2" do |slave2|
    slave2.vm.network "private_network", ip: "192.168.50.7"
    slave2.vm.hostname = "slave2.localdomain"
  end

  config.vm.define "slave3" do |slave3|
    slave3.vm.network "private_network", ip: "192.168.50.8"
    slave3.vm.hostname = "slave3.localdomain"
    config.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.sudo = true
      ansible.limit = "all"
      ansible.playbook = "provisioning/site.yml"
      ansible.groups = {
        "ambari" => ["ambari"],
        "masters" => ["master1", "master2"],
        "slaves" => ["slave1", "slave2", "slave3"]
      }
    end
  end
  
end
