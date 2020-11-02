# Vagrant Minikube for Hyper-V and Virtualbox
Vagrant.configure("2") do |config|
  # VM definitions
  servers=[
      {
        :hostname => "minikube",
        :memory => "4096",
		    :cpu => "4"
      }
    ]
	
  # 
  servers.each do |machine|
   config.vm.define machine[:hostname] do |node|
	  node.vm.box = "centos/7"
	  node.vm.synced_folder ".", "/vagrant"
    node.vm.provider "hyperv" do |hv_node|
      hv_node.memory=machine[:memory]
      hv_node.maxmemory=16384    
      hv_node.cpus=machine[:cpu]
	 	  hv_node.linked_clone = true
		  hv_node.vmname = machine[:hostname]
     end
	   node.vm.provider "virtualbox" do |vb|
		  vb.memory = machine[:memory]
		  vb.cpus = machine[:cpu]
		  vb.linked_clone = true
		  vb.name = machine[:hostname]
	   end 	 
   
    # Update box and install ansible
    $script=<<-SCRIPT
      sudo yum -y update
      sudo yum -y install epel-release   
      yum -y install ansible
    SCRIPT

    # Provisioning 
    node.vm.provision "shell", inline: $script   
    node.vm.provision "file", source: "install-minikube.yml", destination: "install-minikube.yml"
    node.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "install-minikube.yml"
	    ansible.extra_vars = {
			  minikube_version: "1.13.1",
			  docker_version: "19.03.13",
			  kubectl_version: "1.19.2",
			  helm_version: "3.3.4",
			  kubetail_version: "1.6.12"
	    }
    end
   end	
  end 
end