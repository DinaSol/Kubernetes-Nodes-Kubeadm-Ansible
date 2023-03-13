# Kubernetes-Nodes-Kubeadm-Ansible
Configure Kubernetes Cluster using Kubeadm and Ansible

# Configure Linux Machines using Ansible

## Description ## 
- USing Ansible we could configure deploy and configure kubernetes nodes, by running those configurations in the ansible master node

- Here, we have 4 Roles 
   - **Docker Role:**
      - install docker and containerd in master and workers nodes and  enable and start it
   - **firewall Role:**                                                                       
      - Allow ports for kubernetes and container services on master and worker nodes
   - **Kube-depend Role:**                                                                       
      - configure dependencies for kubernetes service and create kubernetes repo

   - **Kubernetes Role:** 
     - instal kubelet, kubectl on nodes
     - enable and start kubelet 
---
## Pre-requisites:
- 2 vms centos 9
- generate ssh keys

   ```bash
     ssh-keygen
   ```
- copy public-ssh-key to the other machines
   ```bash
     ssh-copy-id 192.168.1.138
   ```
- install Ansible on Master node
  ```python
    # Update OS
       sudo yum update

    # Install python3
	    sudo yum install python3
    # Install ansible 
    	sudo yum install epel-release
        sudo yum install ansible

## :warning:  NOTE:
- In ** hosts** ensure that you set the IPs of your master and workers machines

---
## Project Folder Structure 

```python

project
├── hosts
├── playbook.yml
├── README.md
└── roles
    ├── docker
    │   ├── tasks
    │   │   └── main.yml
    ├── firewall
    │   ├── handlers
    │   │   └── main.yml
    │   ├── tasks
    │   │   └── main.yml
    ├── kube-depend
    │   ├── handlers
    │   │   └── main.yml
    │   ├── tasks
    │   │   └── main.yml
    ├── kubernetes
    │   ├── tasks
    │       └── main.yml
    │    
    └── users
        ├── tasks
            └── main.yml
        

```

## Installation


 Use the ansible-playbook to run **playbook.yml** .

   ```bash
    ansible-playbook playbook.yml -i hosts

   ```
