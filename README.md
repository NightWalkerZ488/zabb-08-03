# Домашнее задание к занятию "`ZABBIX`" - `Лоскутов Вячеслав`


### Инструкция по выполнению домашнего задания
   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1 и 2

`Установка Zabbix была произведена с помошью конфигуратора команд с официального сайта, а именно была выбрана версия 7.0 LTS для Debian 12`

``Код для установки и настройки Zabbix:``

``wget https://repo.zabbix.com/zabbix/7.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.0+debian12_all.deb dpkg -i zabbix-release_latest_7.0+debian12_all.deb apt update apt install zabbix-server-pgsql zabbix-frontend-php php8.2-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent sudo -u postgres createuser --pwprompt zabbix sudo -u postgres createdb -O zabbix zabbix zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix systemctl restart zabbix-server zabbix-agent apache2 systemctl enable zabbix-server zabbix-agent apache2`` 
....
....
....


`Снимки экрана`

![Глобальный вид - сервер сконфигурирован и подключены два агента:](https://github.com/NightWalkerZ488/zabb-08-03/blob/main/dash.PNG)

![Подключенные хосты доступны:](https://github.com/NightWalkerZ488/zabb-08-03/blob/main/hosts.PNG)`

![Данные успешно передаются на сервер:](https://github.com/NightWalkerZ488/zabb-08-03/blob/main/data.PNG)
