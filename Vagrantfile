# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vbguest.auto_update = true
  config.vm.synced_folder "#{Dir.home}", '/mnt/shared_home', :mount_options => ["dmode=777,fmode=777"]
  config.vm.define "debian-desktop" do |debian_desktop|
    debian_desktop.vm.hostname = "debian-desktop"
    debian_desktop.vm.box = "debian/buster64"
    debian_desktop.vm.provider "virtualbox" do |vb|
      vb.name = "debian-desktop"
      vb.gui = true
      vb.customize ["modifyvm", :id, "--memory", "2048", "--cpus", "2"]
      #vb.customize ["modifyvm", :id, "--graphicscontroller", "vmsvga"]
      vb.customize ["modifyvm", :id, "--vram", "64"]
      #vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
      #vb.customize ["modifyvm", :id, "--monitorcount", "2"]
      vb.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
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
