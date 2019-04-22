BOX_IMAGE = "bento/ubuntu-16.04"
NODE_COUNT = 2

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false

    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 2
    end
      
    config.vm.define "master" do |master|
        master.vm.box = BOX_IMAGE
        master.vm.network "private_network", ip: "172.16.30.2"
        master.vm.hostname = "master"
        master.vm.provision "ansible" do |ansible|
            ansible.playbook = "ansible/master-playbook.yml"
        end
    end

    (1..NODE_COUNT).each do |i|
        config.vm.define "node-#{i}" do |node|
            node.vm.box = BOX_IMAGE
            node.vm.network "private_network", ip: "172.16.30.#{i + 2}"
            node.vm.hostname = "node-#{i}"
            node.vm.provision "ansible" do |ansible|
                ansible.playbook = "ansible/node-playbook.yml"
            end
        end
    end
end 