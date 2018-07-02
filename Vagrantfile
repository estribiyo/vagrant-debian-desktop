# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "debian-desktop" do |debian_desktop|
    debian_desktop.vm.hostname = "debian-desktop"

    debian_desktop.vm.box = "debian/stretch64"

    debian_desktop.vm.provider "virtualbox" do |vb|
      vb.name = "debian-desktop"
      vb.gui = true
      vb.memory = "3072"
      vb.customize ["modifyvm", :id, "--vram", "128"]
    end

    debian_desktop.vm.provision "ansible_local" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.install_mode = "pip_args_only"
      ansible.pip_args = "-r /vagrant/requirements.txt"
      ansible.become = true

      ansible.config_file = "ansible.cfg"
      ansible.playbook = "debian-desktop.yml"
    end
  end
end
