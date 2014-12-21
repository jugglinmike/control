# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "chef/debian-7.7"

  config.vm.network "private_network", ip: "192.168.1.64"

  config.vm.provision "ansible" do |ansible|
    ansible.limit = "vagrant"
    ansible.verbose = "vvvv"
    ansible.ask_sudo_pass = true
    ansible.inventory_path = "deploy/inventory/development"
    ansible.playbook = "deploy/01-harden.yml"
  end
end
