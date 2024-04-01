# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Андрющенко Вячеслав`


---

### Задание 1  

Установите Zabbix Server с веб-интерфейсом.   

Процесс выполнения

Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.

Установите PostgreSQL. Для установки достаточна та версия, что есть в системном репозитороии Debian 11.

Пользуясь конфигуратором команд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache.

Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server.

Требования к результаты

Прикрепите в файл README.md скриншот авторизации в админке.

Приложите в файл README.md текст использованных команд в GitHub.
   

### Решение 1  
![Авторизация](/img/auth.png)

#### Список команд  
1) wget https://repo.zabbix.com/zabbix/6.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.4-1+ubuntu22.04_all.deb
2) dpkg -i zabbix-release_6.4-1+ubuntu22.04_all.deb
3) apt update
4) apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
5) apt install postgresql
6) sudo -u postgres createuser --pwprompt zabbix
7) sudo -u postgres createdb -O zabbix zabbix
8) zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
9) nano /etc/zabbix/zabbix_server.conf , редактируем DBPassword=password
10) systemctl restart zabbix-server zabbix-agent apache2
11) systemctl enable zabbix-server zabbix-agent apache2
---

### Задание 2
