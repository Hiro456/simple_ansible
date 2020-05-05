# Code_Challenge_Infrastructure_as_a_Code

Prerequisiti:
- aver installato ansible (testato con ansible 2.9.7)
- aver installato vagrant (testato con vagrant 2.2.7)
    - vagrant plugin install vagrant-disksize
- pip install jmespath

# TRIP
- On local machine:
- $ vagrant up
- To re-run a playbook on an existing VM, just run:
- $ vagrant provision
- On machine 1 ( $ vagrant ssh machine1):
- $ docker node ls
- $ docker service create --replicas 2 alpine ping 8.8.8.8
- $ docker service ls
- $ docker node update --role manager machine2
- On machine 2 ( $ vagrant ssh machine2):
- $ docker node ls

# Test REST API form local machine:
- curl http://172.20.0.201:4243/containers/json
- crul http://172.20.0.202:4243/containers/json

# TODO
- aggiungere sicurezza, attualmente tutto semplice
- aggiungere test
- completare documentazione