## Fabio Load balancer backed by Consul example

### Requirements

* Installed Ansible
* Installed Vagrant
* Vagrant nodes up and running: 
```bash
cd vagrant && vagrant up
```


## Infrastructure setup

#### Configure load balancer

```bash
ansible-playbook -i ansible/inventory/local ansible/lb.yml -vvvv
```

#### Configure applications servers

```bash
ansible-playbook -i ansible/inventory/local ansible/ap.yml -vvvv
```


## Tests

To check if everything works:
```bash
curl http://192.168.56.110:9999/foo
```

Should return:
```
Serving /foo from ap01 on 192.168.56.101:9000
```
or:
```
Serving /foo from ap02 on 192.168.56.102:9000
```

### Cluster 

To check cluster and services status open [LINK](http://192.168.56.110:8500/ui/)