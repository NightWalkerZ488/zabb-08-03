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

### Задание 1

`Установка Zabbix была произведена с помошью конфигуратора команд с официального сайта, а именно была выбрана версия 7.0 LTS для Debian 12`

### Шаг 1 - установка репозитория Zabbix:
1. wget https://repo.zabbix.com/zabbix/7.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.0+debian12_all.deb
2. dpkg -i zabbix-release_latest_7.0+debian12_all.deb
3. apt update

### Шаг 2 - создание базы данных:

1. sudo -u postgres createuser --pwprompt zabbix
2. sudo -u postgres createdb -O zabbix zabbix

### Шаг 3 - На хосте Zabbix сервера импортируем начальную схему и данные:

1. zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix


### Шаг 4 - установка пароля в файле zabbix_server.conf и запуск сервера с агентом:

1. nao 	/etc/zabbix/zabbix_server.conf  (задаём параметр "DBPassword=")
2. systemctl restart zabbix-server zabbix-agent apache2
3. systemctl enable zabbix-server zabbix-agent apache2


### `Снимок экрана успешной авторизации в админке Zabbix:`

![Глобальный вид - сервер сконфигурирован и подключены два агента:](https://github.com/NightWalkerZ488/zabb-08-03/blob/main/dash.PNG)

### `Команды, использованные для Git:`

1. Git clone https://github.com/NightWalkerZ488/zabb-08-03/tree/ - создаём локальную копию репозитория.
2. Git add README.md - добавляем файл для ослеживания изменений. Также добавляем файлы снимков экрана - "git add dash.png".
3. После заполнения файла README.md вводим "git commit" и "пушим" изменения на сервер "gip push".
4. Проверяем в git-репозитории корректное отображение нового содержимого файла README.md

# `Задание 2`

### Шаг 1 - Установка на хосты Zabbix агента: 

1. wget https://repo.zabbix.com/zabbix/7.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.0+debian12_all.deb
2. dpkg -i zabbix-release_latest_7.0+debian12_all.deb
3. apt update
4. apt install zabbix-agent

### Шаг 2 - запуск прцесса Zabbiz агента:

1. systemctl restart zabbix-agent
2. systemctl enable zabbix-agent

### Шаг 3 - добавление хостов на Zabbix сервере:

### `Снимок экрана раздела "Узлы сети", где видно, что оба узла(хоста) довалены, и агенты подключены: ` 

![Подключенные хосты доступны:](https://github.com/NightWalkerZ488/zabb-08-03/blob/main/hosts.PNG)`

### `Снимок экрана раздела открытого файла лога zabbox агента, где видно, что агент работает:` 

![Log агента:](https://github.com/NightWalkerZ488/zabb-08-03/blob/main/log.PNG)`

### `Снимок экрана раздела "Последние данные", где видно, что данные от обоих узлов поступают, и видно количество метрик от каждого узла:` 

![Метрики узла 1:](https://github.com/NightWalkerZ488/zabb-08-03/blob/main/agent1.PNG)`

![Метрики узла 2:](https://github.com/NightWalkerZ488/zabb-08-03/blob/main/agent2.PNG)`

### Шаг 4 - добавляем новые снимки экрана в git-репозиторий, дополняем файл README.md и "коммитим", "пушим" всё в Git:

1. Git add log.png, agent1.png, agent2.png
2. Git commit
3. Git push.
