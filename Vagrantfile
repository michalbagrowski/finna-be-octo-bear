# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|


  config.vm.define "master" do |master|
    master.vm.provision "shell",  inline: "echo MASTER"
    master.vm.box = "ubnt-server"
    master.vm.network "forwarded_port", guest: 8080, host: 8081
    master.vm.provision "ansible" do |ansible|
      ansible.playbook = "master.yml"
      ansible.inventory_path = "master_hosts"
      ansible.limit = "all"
    end
  end

  config.vm.define "slave" do |slave|
    slave.vm.provision "shell", inline: "echo SLAVE"
    slave.vm.box = "ubnt-server"
    slave.vm.network "forwarded_port", guest: 8080, host: 8082


    slave.vm.provision "shell", inline: "echo SLAVE"

    slave.vm.provision "ansible" do |ansible|
      ansible.playbook = "slave.yml"
      ansible.inventory_path = "slave_hosts"
      ansible.limit = 'all'
    end

  end
  
end
