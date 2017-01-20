# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos/7"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/main.yml"
    ansible.verbose = "v"
    ansible.sudo = true
#    ansible.become = true
#    ansible.become_method='sudo'
    end
  
  config.vm.define "db1" do |db1|
    db1.vm.hostname = "db1"
    db1.vm.network "private_network", ip: "192.168.50.101"
  end

  config.vm.define "db2" do |db2|
    db2.vm.hostname = "db2"
    db2.vm.network "private_network", ip: "192.168.50.102"
  end

  config.vm.define "db3" do |db3|
    db3.vm.hostname = "db3"
    db3.vm.network "private_network", ip: "192.168.50.103"
  end

  config.vm.define "maxscale" do |maxscale|
    maxscale.vm.hostname = "maxscale"
    maxscale.vm.network "private_network", ip: "192.168.50.104"
    maxscale.vm.network "forwarded_port", guest_ip: "192.168.50.104", guest:4008, host:3308
  end

  config.vm.provider "virtualbox" do |v|
    v.memory = 512
    v.cpus = 1
  end

#  config.ssh.password = "vagrant"

end
