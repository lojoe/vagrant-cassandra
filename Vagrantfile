# -*- mode: ruby -*-
# vi: set ft=ruby :

NUM_NODES = 1
CPUS_PER_NODE = 1
MEMORY_PER_NODE = 1024


Vagrant.configure(2) do |config|
    config.vm.box = "parallels/centos-6.6"
    config.vm.network "private_network", type: "dhcp"

    (1..NUM_NODES).each do |k|
        name = "cassandra-#{k}"
        config.vm.define name do |node|
            node.vm.hostname = name
            node.vm.provider "parallels" do |provider|
                provider.name = "vagrant-#{name}"
                provider.cpus = CPUS_PER_NODE
                provider.memory = MEMORY_PER_NODE
            end
        end
    end

    config.vm.provision "ansible" do |ansible|
        ansible.sudo = true
        ansible.playbook = "ansible/site.yml"
        ansible.groups = {
            "cassandra" => (1..NUM_NODES).map {|i| "cassandra-#{i}"}
        }
    end
end
