# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "box-cutter/ubuntu1404-i386"
  config.vm.hostname = "web"
  config.vm.network "private_network", ip: "10.0.0.10"
  config.vm.synced_folder ".", "/vagrant"
  config.vm.boot_timeout = 600
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
    vb.name = "web"
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.install_mode = "pip"
    ansible.playbook = "playbook.yml"
    ansible.groups = {
      "webservers" => ["web"],
      "dbservers" => ["web"]
    }
  end
end
