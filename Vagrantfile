
$nVM = 2

Vagrant.configure(2) do |config|
    config.vm.box = "centos/7"
    config.ssh.forward_agent = true
    config.disksize.size = '80GB'

    (1..$nVM).each do |vm_id|
      config.vm.define "machine#{vm_id}" do |machine|
        machine.vm.hostname = "machine#{vm_id}"
        machine.vm.network "private_network", ip: "172.20.0.#{200+vm_id}"
        machine.vm.provider "virtualbox" do |v|
          v.name = "machine#{vm_id}"
        end

        if vm_id == $nVM
          machine.vm.provision :ansible do |ansible|
            ansible.limit = "all"
            #ansible.verbose = "v"
            ansible.playbook = "ansible/defaults/project_setup.yml"
            ansible.groups = {
                "docker_engine" => ["machine[1:2]"],
                "docker_swarm_manager" => ["machine1"],
                "docker_swarm_worker" => ["machine2"]
                }
          end
        end
      end
    end
end