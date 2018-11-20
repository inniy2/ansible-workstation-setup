## Deploy vagrant  

- - - -  
#### Version dependency  
1. Ansible: `2.5.1`
2. Python:  `3.6.5`


- - - -  
#### Role dependency  
```
None
```


- - - -  
#### VARS
inside `group_vars/hostgroup` 


```yml
---
home_dir: "/Users/XXXXXX"
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

- - - -  
#### Playbook example  


```yml
---
# This play book deploy OS to Vagrant

- hosts: workstation
  become: no

  environment:
    PATH: "/usr/local/bin:{{ ansible_env.PATH }}:$PATH"

  roles:
    - deploy-os
```



