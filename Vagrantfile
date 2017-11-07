# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"

  config.vm.synced_folder ".", "/vagrant", type: 'virtualbox'

  config.vm.network "public_network"

  config.vm.provision "shell", inline: <<-SHELL
    if [ ! -f /etc/apt/sources.list.d/ansible.list ]; then
      echo 'deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main' >> /etc/apt/sources.list.d/ansible.list
      apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
    fi
    apt-get update
    apt-get install -y --allow-unauthenticated ansible
  SHELL
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y dirmngr avahi-utils
  SHELL
  config.vm.provision "shell", inline: <<-SHELL
    apt-get install -y zsh zsh-antigen git vim cscope exuberant-ctags
    chsh -s /usr/bin/zsh vagrant
  SHELL
  config.vm.provision "file", source: "~/.zshrc", destination: "$HOME/.zshrc"
  config.vm.provision "file", source: "~/.zsh", destination: "$HOME/.zsh"
#  config.vm.provision "shell", privileged: false, inline: <<-SHELL
#  SHELL
end

