# -*- mode: ruby -*-
# vi: set ft=ruby :

unless Vagrant.has_plugin?("vagrant-vbguest")
  puts 'Installing vagrant-vbguest Plugin...'
  system('vagrant plugin install vagrant-vbguest')
end

Vagrant.configure("2") do |config|
  config.vbguest.auto_update = true
  config.vm.synced_folder ENV["HOME"], "/mnt/shared_home", id: "shared_home", automount: true
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
      vb.customize ["storageattach", :id, "--storagectl", "SATA Controller", "--port", "1", "--device", "0", "--type", "dvddrive", "--medium", "emptydrive"]
    end
    debian_desktop.vm.provision "ansible_local" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.become = true
      ansible.config_file = "ansible.cfg"
      ansible.install_mode = "pip3"
      ansible.version = "2.7.7"
      ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }
      # playbook settings
      ansible.playbook = "debian-desktop.yml"
      ansible.limit = "all"
    end
  end
end
