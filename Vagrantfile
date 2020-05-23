# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.box = "hashicorp/bionic64"

  config.vm.network "forwarded_port", guest: 8080, host: 8080, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 7077, host: 7077, host_ip: "127.0.0.1"


  config.vm.network "private_network", ip: "192.168.10.101"

  config.vm.hostname = "managervm"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # hostdir, guestdir
  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider "virtualbox" do |vb|
   vb.memory = "1024"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    #ansible.become = true
    ansible.playbook = "playbook.yml"
  end

end
