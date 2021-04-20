BOX_IMAGE = "ubuntu/xenial64"
# NODE_COUNT controls how many webserververs are created.The haproxy config currently only allows for two nodes.
NODE_COUNT = 2
CPU_COUNT = 1
MEMORY_SIZE = 512

Vagrant.configure("2") do |config|
#Build webserver node VMs
  (1..NODE_COUNT).each do |i|
    config.vm.define "node#{i}" do |subconfig|
      subconfig.vm.box = BOX_IMAGE
      subconfig.vm.hostname = "node#{i}"
      subconfig.vm.network :private_network, ip: "10.0.0.#{i + 10}"
      # configure provider (#set vcpu and memory to save resources on host)
      subconfig.vm.provider "virtualbox" do |vb|
        vb.cpus = CPU_COUNT
	vb.memory = MEMORY_SIZE
      end
      #following line used for bootsrap file. using ansible playbook instead.
      #subconfig.vm.provision "shell", path: "bootstrap/node_bootstrap.sh"
      subconfig.vm.provision :ansible_local do |ansible|
        ansible.verbose = "v"
	ansible.playbook = "provision/playbook_web.yml"
      end
    end
  end
  
 # Build haproxy load balancer VM
  config.vm.define "LB" do |subconfig|
    subconfig.vm.box = BOX_IMAGE
    subconfig.vm.hostname = "LB"
    subconfig.vm.network :private_network, ip: "10.0.0.10"
    # configure provider (#set vcpu and memory to save resources on host)
    subconfig.vm.provider "virtualbox" do |vb|
      vb.cpus = CPU_COUNT
      vb.memory = MEMORY_SIZE
    end
    #following line used for bootsrap file. using ansible playbook instead.
    #subconfig.vm.provision "shell", path: "bootstrap/node_bootstrap.sh"
    subconfig.vm.provision :ansible_local do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "provision/playbook_lb.yml"
   end
  end
end
