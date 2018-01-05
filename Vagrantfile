Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"
  config.vm.host_name = "debian9-desktop"

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
	
    # ansible.verbose = "vvv"
  end
  
  config.vm.provider "virtualbox" do |vb|
	vb.name = "debian9-desktop"
    vb.memory = "3072"
	
	vb.gui = true
  end
  
  config.vm.box_check_update = false
end
