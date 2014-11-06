# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define :haproxy1 do |haproxy1|
    haproxy1.vm.hostname = "haproxy1"
    haproxy1.vm.box = "ubuntu/trusty64"
    haproxy1.vm.network :private_network, ip: "192.168.40.10"
    haproxy1.vm.synced_folder ".", "/vagrant"
    haproxy1.vm.provider "virtualbox" do |vm|
      vm.customize ["modifyvm", :id, "--memory", 2048, "--cpus", 2]
      vm.gui = false
    end
    haproxy1.vm.provision "ansible" do |ansible|
        ansible.sudo = true
        ansible.verbose = "v"
        ansible.playbook = "site.yml"
		ansible.extra_vars = { keepalived_priority: 100 }
    end
  end
  config.vm.define :haproxy2 do |haproxy2|
    haproxy2.vm.hostname = "haproxy2"
    haproxy2.vm.box = "ubuntu/trusty64"
    haproxy2.vm.network :private_network, ip: "192.168.40.11"
    haproxy2.vm.synced_folder ".", "/vagrant"
    haproxy2.vm.provider "virtualbox" do |vm|
      vm.customize ["modifyvm", :id, "--memory", 2048, "--cpus", 2]
      vm.gui = false
    end
    haproxy2.vm.provision "ansible" do |ansible|
        ansible.sudo = true
        ansible.verbose = "v"
        ansible.playbook = "site.yml"
		ansible.extra_vars = { keepalived_priority: 101 }
    end
  end
end
