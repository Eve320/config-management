# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|
# General Vagrant VM configuration.
  config.vm.box = "geerlingguy/ubuntu2004"
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.provider :virtualbox do |v|
    v.memory = 2048
    v.linked_clone = true
  end

  # Frontend server
  config.vm.define "client" do |app|
    app.vm.hostname = "client"
    app.vm.network :private_network, ip: "192.168.60.7"
  end

  # Backend server
  config.vm.define "backend" do |app|
    app.vm.hostname = "backend"
    app.vm.network :private_network, ip: "192.168.60.8"
  end

  # Mongodb server
  config.vm.define "mongodb" do |db|
     db.vm.hostname = "mongodb"
    db.vm.network :private_network, ip: "192.168.60.9"
  end

  # Provisioning configuration for Ansible.
  config.vm.provision "ansible" do |ansible|
  ansible.playbook = "playbook.yml"
  end

end

