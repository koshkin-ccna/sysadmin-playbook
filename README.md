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

### monitoring-prometheus-grafana.yml

```console
ansible-galaxy install \
    cloudalchemy.node-exporter \
    cloudalchemy.prometheus \
    cloudalchemy.grafana
ansible-playbook user-create-centos.yml
```

This playbook installs Prometheus and Grafana to the CentOS server.

+ Add monitored hosts to /etc/hosts
+ Install Node Exporter to localhost
+ Install Prometheus version 2.12.0
+ Install Grafana version 6.3.3
+ Add dashboards to Grafana

This playbook uses three roles from cloudalchemy, so you have to install them before running this playbook.

### monitoring-netdata.yml

This playbook installs Netdata and configures the notification for the local machine. Real-time monitoring from the web interface on port 19999 of the localhost. It has a prometheus-like builtin exporter if you want to scrape data from netdata.

> Netdata is an open source tool to visualize and monitor real-time metrics, optimized to accumulate all types of data, such as CPU usage, disk activity, SQL queries, visits to a website, etc

+ Install epel repository
+ Download netdata Install script
+ Execute Netdata install script
+ Enable netdata systemd service
+ Create alarm config from sample file
+ Configure Slack and Pushbullet notifications
+ Send test notifications to sysadmin

### user-create-centos.yml

```console
ansible-playbook user-create-centos.yml
```

playbook tested on CentOS 7.6.1810 (Core)

+ Install zsh package
+ Create user without password
+ Put ssh public keys
+ Allow passwordless sudo
