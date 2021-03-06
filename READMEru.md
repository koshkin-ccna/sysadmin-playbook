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

Устанавливает сервис Netdata и конфигурирует отправку алертов с локальной машины. Netdata предоставляет веб-интерфейс на порт 19999. Также можно настроить вывод данных в формате экспортера для Prometheus.

+ Установить epel репозитория
+ Скачать скрипт установки Netdata
+ Выполнить скрипт установки
+ Включить сервис на запуск после перезагрузки
+ Создать конфиг для отправки алертов
+ Настроить алерты для Slack и Pushbullet
+ Отправить тестовые алерты группе sysadmin

### user-create-centos.yml

> $ ansible-playbook user-create-centos.yml

Проверен на CentOS 7.6.1810 (Core)

+ Установить пакет zsh
+ Создать нового пользователя
+ Положить публичные ssh ключи для авторизации
+ Разрешить sudo без пароля
