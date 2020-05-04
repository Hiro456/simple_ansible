# Code_Challenge_Infrastructure_as_a_Code

Prerequisiti:
- aver installato ansible
- aver installato vagrant (e quindi anche virtual box) => 1.8 (https://www.vagrantup.com/docs/provisioning/ansible_intro.html)
    - vagrant plugin install vagrant-disksize
- ansible-galaxy install suzuki-shunsuke.docker_ce_centos
- ansible-galaxy install atosatto.docker-swarm https://galaxy.ansible.com/atosatto/docker-swarm
-pip install jmespath


To start the vm run
vagrant up

To re-run a playbook on an existing VM, just run:
vagrant provision


LOCAL TEST
vagrant ssh machine1
docker node ls
docker service create --replicas 2 alpine ping 8.8.8.8
docker service ls
vagrant ssh machine1
docker node update --role manager machine2
docker node ls

Test REST API form local machine:
http://172.20.0.201:4243/containers/json
http://172.20.0.202:4243/containers/json

# TODO
- aggiungere sicurezza, attualmente tutto semplice