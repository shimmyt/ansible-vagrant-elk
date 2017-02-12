Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"

  config.vm.provider "virtualbox" do |vb|
     # Display the VirtualBox GUI w"hen booting the machine
     vb.gui = true
  
     # Customize the amount of memory on the VM:
     vb.memory = 1024
     vb.cpu = 1
  end

  config.vm.define "data01"
  config.vm.define "web01"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "elk.yml"
    ansible.groups = {
      "elasticsearch" => ["data01","web01"]
      "nginx" => ["web01"]
      "logstash" => ["data01"]
      "kibana" => ["web01"]
    }
  end
end
