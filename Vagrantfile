
$nVM = 2
$instance_name_prefix = "vmCentos"

Vagrant.configure(2) do |config|
    config.vm.box = "centos/7"
    config.ssh.forward_agent = true
    config.disksize.size = '80GB'

    (1..$nVM).each do |vm_id|
      config.vm.define "machine#{vm_id}" do |machine|
        machine.vm.hostname = "machine#{vm_id}"
        machine.vm.network "private_network", ip: "172.20.0.#{200+vm_id}"
        machine.vm.network "public_network", bridge: 'bridge0', ip: "192.168.1.#{vm_id+200}"

        if vm_id == $nVM
          machine.vm.provision :ansible do |ansible|
            ansible.limit = "all"
            ansible.playbook = "ansible/project_setup.yml"
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