Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision/playbook.yml"
  end
  # vbox settings
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", 4096]
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
    vb.customize ["modifyvm", :id, "--cpus", 2]
  end
  # network settings
  config.vm.hostname = "vagrant.machine"
  config.vm.network "private_network", ip: "192.168.100.33"
  config.vm.network "forwarded_port", guest: 22, host: 2222, id: "ssh", auto_correct: true
  config.vm.network "forwarded_port", guest: 80, host: 8000, id: "http", auto_correct: true
  # to be continued
end
