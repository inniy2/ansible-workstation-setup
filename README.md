## Ansible workstation

- - - -  
###### Version denpendencies  
1. OSX: `10.12.6`  
2. Vagrant: `2.1.1`  
3. VirtualBox: `5.2.12 r122591 (Qt5.6.3)`  
4. Python: `2.7.10`  
5. Pipenv: `11.9.0`  
6. Virtualenv:  
  - Python: `3.6.5`  
  - Ansible: `2.5.1`  
  

- - - -  
1. Example for running playbooks  
```bash
cd ~/playbooks/ansible-workstation-setup

# Deploy CentOS with vagrant
ansible-playbook deploy_os.yml


# Destroy VM
ansible-playbook destroy_os.yml
```


- - - -  
2. Example for running adhoc commandline  
```bash
cd ~/playbooks/ansible-workstation-setup

ansible vagrant  -m shell -a "ls -al /tmp"

ansible node1    -m shell -a "ls -al /tmp"
```


- - - -  
3. Configuration example  
```bash
vim ~/playbooks/workstation


[workstation]
127.0.0.1

[workstation:vars]
ansible_connection=ssh
ansible_ssh_user=
ansible_ssh_pass=
```


```bash
vim ~/playbooks/vagrant

[vagrant:children]
node1
node2
node3
node4
node5
node6

[vagrant:vars]
ansible_connection=ssh
ansible_ssh_user=vagrant
ansible_ssh_pass=vagrant


[node1]
192.168.33.11

[node2]
192.168.33.12

[node3]
192.168.33.13

[node4]
192.168.33.14

[node5]
192.168.33.15

[node6]
192.168.33.16
```


```bash
vim ~/playbooks/ansible-workstation/group_vars/workstation.yml

---
home_dir: "/Users/XXXX"
git_home: "{{ home_dir }}/Documents/git"
vagrant_dir: "{{ git_home }}/Vagrant"
c_class_ip: "192.168.33"

node_directories:
  node11:
    ip: 192.168.33.11
  node12:
    ip: 192.168.33.12
  node13:
    ip: 192.168.33.13
  node14:
    ip: 192.168.33.14
  node15:
    ip: 192.168.33.15
  node16:
    ip: 192.168.33.16
```

