IMAGE = "ubuntu/focal64"

Vagrant.configure("2") do |config|
  config.vm.define "control", primary: true do |subconfig|
    subconfig.vm.box = IMAGE
    subconfig.vm.hostname = "control"
    subconfig.vm.network :private_network, ip: "192.168.56.50"
    subconfig.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end
  
  config.vm.define "node1" do |subconfig|
    subconfig.vm.box = IMAGE
    subconfig.vm.hostname = "node1"
    subconfig.vm.network :private_network, ip: "192.168.56.51"
  end

  config.vm.define "node2" do |subconfig|
    subconfig.vm.box = IMAGE
    subconfig.vm.hostname = "node2"
    subconfig.vm.network :private_network, ip: "192.168.56.52"
  end

  # Install avahi on all machines  
  config.vm.provision "shell", inline: <<-SHELL
    apt-get install -y avahi-daemon libnss-mdns
  SHELL
  
end
