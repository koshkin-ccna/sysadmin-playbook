# sysadmin-playbook

 Ansible playbooks for everyday sysadmin tasks 

## Prereq

+ Install Ansible
+ Install Ansible Galaxy roles (see roles section in each playbook)
+ Edit `inv.yml` file to correspond with your target hosts
  + or remove `inv.yml` and `ansible.cfg` files to use your global ansible inventory file
+ Edit `hosts` line in each playbook to configure target host(s)


## Description

Playbooks are configured to use `vagrant-centos` target host by default with ssh connection pointed to 127.0.0.1:2222 and `~/.ssh/privatekey.pem` key.

Playbooks are tested on CentOS 7.6 image from vagrant repo maintained by geerlingguy `geerlingguy/centos7  (virtualbox, 1.2.18)`

## Usage

```console
ansible-galaxy install name.rolename # install role from Ansible Galaxy
ansible-playbook playbook-file.yml # execute playbook
ansible-playbook -vvv playbook-file.yml # max verbosity
```

### certbot-nginx.yml

$ ansible-playbook certbot-nginx.yml

### default-software.yml

### docker-install.yml

### monitoring-alertmanager.yml

### monitoring-netdata.yml