Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"
  config.vm.host_name = "debian9-desktop"

  config.vm.provision "ansible_local" do |ansible|
	ansible.compatibility_mode = "2.0"
	ansible.become = true
	
    ansible.playbook = "default.yml"
	
    # ansible.verbose = "vvv"
  end
  
  config.vm.provider "virtualbox" do |vb|
	vb.name = "debian9-desktop"
	vb.gui = true
    vb.memory = "3072"
	vb.customize ["modifyvm", :id, "--vram", "128"]
  end
  
  config.vm.box_check_update = false
end
