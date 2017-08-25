# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"

  config.vm.network "public_network"

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y dirmngr avahi-utils
    echo 'deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main' >> /etc/apt/sources.list
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
    apt-get update
    apt-get install -y ansible
  SHELL
end
