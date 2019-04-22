# Kubernetes Setup Using Ansible and Vagrant

A complete local Kubernetes cluster with one master and two workers for testing purposes. Ansible playbooks will be used for provisioning.

## Prerequisites

Vagrant : https://www.vagrantup.com/downloads.html  
VirtualBox : https://www.virtualbox.org/wiki/Downloads  
Ansible: https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html  

## Setup overview

`Vagrant up` will deploy one master node and two workers using Ubuntu Xenial with 2 CPUs and 1GB of memory with static IPs: 

- master 172.16.30.2
- node-1 172.16.30.3
- node-2 172.16.30.4


```
vagrant status
Current machine states:

master                    running (virtualbox)
node-1                    running (virtualbox)
node-2                    running (virtualbox)
```

Ansible playbooks will provision all necessary packages, initialize the master and join the nodes to Kubernetes cluster. 

The kubernetes cluster have the following features by default:
- Kubernetes control plane (1.13.1)
- Calico networking CNI
- kubectl bash completion


To setup this cluster: 

```
https://github.com/melina/k8s-homelab.git
cd k8s-homelab
vagrant up
```

Kubernetes cluster should be up and running: 


```
kubectl get nodes
NAME     STATUS   ROLES    AGE    VERSION
master   Ready    master   115m   v1.13.1
node-1   Ready    <none>   87m    v1.13.1
node-2   Ready    <none>   84m    v1.13.1
```










