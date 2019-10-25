# sysadmin-playbook

 Репозиторий с Ansible плейбуками для выполнения частых задач в системном администрировании.

## Подготовка окружения

+ Установить Ansible
+ Установить роли из Ansible Galaxy (см. в плейбуке секцию roles)
+ Отредактировать файл `inv.yml`, указать там свои целевые хосты
  + либо удалить файлы `inv.yml` и `ansible.cfg` чтобы использовать глобальный конфиг и файл инвентаризации
+ Отредактировать строку `hosts` в плейбуке, чтобы указать целевой(ые) хосты


## Описание

В плейбуках в качестве целевого хоста указан `vagrant-centos` с подключением ssh по адресу 127.0.0.1:2222 и публичным ключом `~/.ssh/privatekey.pem`.

Работоспособность плейбуков была протестирована на CentOS 7.6 из Vagrant репозитория разработчика geerlingguy `geerlingguy/centos7  (virtualbox, 1.2.18)`

## Использование

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