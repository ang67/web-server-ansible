# web-server-ansible

## Install Ansible

```bash
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo add-apt-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```

## Install vagrant instance

## Create and copy ssh key on web server

```bash
$ ssh-keygen -t rsa -b 4096
$ ssh-copy-id -i ~/.ssh/id_rsa.pub  vagrant@100.0.0.10
```
## First task
- Build hosts

```
[web]
100.0.0.10
```

- Write the playmook.yml for installing Git

```
---
- name: Installing web servers
  hosts: web
  remote_user: root
  tasks:
    - name: Installating Git
      apt: name=git state=latest
```

- Run playbook

```bash
$ ansible-playbook -i hosts playbook.yml
```