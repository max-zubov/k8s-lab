

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false
    ssh_prv_key = ""
    ssh_pub_key = ""
    config.vm.synced_folder "./", "/vagrant", owner: "vagrant", mount_options: ["dmode=775,fmode=600"]

  
    config.vm.define "vm1" do |vm1|
      vm1.vm.box = "bento/centos-8.2"
      vm1.vm.network  "private_network", ip: "192.168.33.51"
      vm1.vm.hostname = "ansible-vm"
      vm1.vm.provision "shell", inline: <<-'SCRIPT'
        dnf -y update
        dnf -y install python3
        pip3 install ansible
      SCRIPT
      vm1.vm.provider "virtualbox" do |vb|
        vb.name = "ansible-vm"
        vb.memory = "1024"
      end
    end
end
