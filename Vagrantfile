# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "puppetlabs/centos-6.6-64-nocm"
  config.vm.box_check_update = false
  config.ssh.insert_key = false
 
  config.vm.provider "docker" do |vb|
    vb.customize ["modifyvm", :id, "--memory", 1280 ]
    vb.customize ["modifyvm", :id, "--cpus", 1 ]
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
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
      ansible.inventory_path = "provisioning/inventory"
      ansible.verbose = "v"
      ansible.sudo = true
      ansible.limit = "all"
      ansible.playbook = "provisioning/site.yml"
    end
  end
  
end
