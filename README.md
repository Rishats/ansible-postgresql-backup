Playbooks for usage example:
=========

1) Edit hosts file.
2) Edit group_vars all.yml
3) Ping your hosts 
```bash
ansible-playbook -i hosts -e "servers=all" playbooks/ping.yml
```
4) Install PostgreSQL Backup App
```bash
ansible-playbook -i hosts -e "servers=all" roles/ansible_postgresql_backup/ansible_postgresql_backup.yml
```


# Develop purpose:
Vagrantfile:
=========
By default Vagrantfile create 2 VMs based on Centos Stream 8 and Ubuntu 20.04 LTS.

1) Create and ping your hosts 
```bash
vagrant up # create VMs

ansible-playbook -i hosts -e "servers=all" playbooks/ping.yml # Ping VMs
```
2) Install PostgreSQL Backup App 
```bash
ansible-playbook -i hosts -e "servers=all" roles/ansible_postgresql_backup/ansible_postgresql_backup.yml
```
3) Install PostgreSQL on hosts *(Optional)*
```bash
ansible-playbook -i hosts -e "servers=all" playbooks/ansible-role-postgresql.yml
```
4) Work with VMs

```bash
ssh vagrant@192.168.50.2 # centos stream 8
sudo su backuper # our your user
crontab -l # check crontab record if need run code manual

ssh vagrant@192.168.50.3 # ubuntu 20.04.03 LTS
sudo su backuper # our your user
crontab -l # check crontab record if need run code manual
```


### Destory develop stage:
```bash
vagrant destroy -f
```
