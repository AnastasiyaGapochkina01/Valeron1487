# Работа с файлами и директориями
1) В домашнем каталоге создать каталог lab1. В каталоге lab1 создать директорию library
2) В каталоге library создать каталоги division и authors
3) Перейти в каталог division, создать в нем директории fiction, detective, textbook
4) Не переходя в директорию authors создать в ней директорию bradbury_r, tanenbaum_s, christie_a
5) Перейти в директорию library/authors/tanenbaum_s, создать файл computer_networks и записать в него текст
```
ISBN-13: 978-0-13-212695-3
ISBN-10: 0-13-212695-8
Computer networks / Andrew S. Tanenbaum
```
6) В директории christie_a создать файл crooked_house с текстом
```
ISBN: -
Agatha Christie Limited
```
7) В директории bradbury_r создать файл the_martian_chronicles с текстом
```
ISBN: 978-1-4516-7819-2
Ray Bradbury
```
8) Скопировать файл crooked_house в detective
9) Скопировать файл computer_networks в textbook
10) Скопировать файл the_martian_chronicles в fiction
11) В каталоге lab1 создать директорию library_archive
12) Скопировать содержимое директории library в library_archive
13) Перейти в library_archive и сделать копию папки authors с новым именем authors_bk
14) Создать папку backups и переместить туда authors_bk
15) Удалить директорию backups
16) Удалить все в library_archive
# Работа с текстом
1) Создать в домашней директории папку home_works
2) В директории home_works создать директорию text_processing
3) В директории text_processing создать файл info.csv с таким содержимым
```
Name:Company:Price:Ganre:Multiplayer
Item1:Company1:60000$:Ganre1:Yes
Item2:Company2:70000$:Ganre2:Yes
Item3:Company3:90000$:Ganre1:Yes
Item4:Company4:90000$:Ganre1:No
Item5:Company5:110000$:Ganre1:Yes
Item6:Company6:410000$:Ganre2:Yes
Item7:Company1:60000$:Ganre1:Yes
Item8:Company4:40000$:Ganre2:No
Item9:Company3:90000$:Ganre1:Yes
```
4) В файле info.csv с помощью grep найти строки, которые содержат слово No
5) В файле info.csv найти все строки, в которых встречается слово Ganre2
6) В файле info.csv найти все строки, в которых встречается слово Ganre2 и вывести только 3 поле
7) В директории text_processing создат файл metrics с содержимым
```
metric_name:metric_type:interval
cache_disk_use:gauge:1
cache_use:gauge:0
key_buffer_bytes_used:byte:3
table.rows.read:count:10
disk_use:gauge:10
data_size:gauge:1
rows_deleted:count:1
bytes_received:byte:1
```
8) В файле metrics найти все строки, в которых встречается слово gauge и вывести только первое поле
9) В файле metrics найти все строки, в которых встречается слово byte и вывести только 3 поле
10) В файле metrics найти все строки, в которых встречается слово disk и вывести только 2 поле
11) В файле metrics найти все строки, которые начинаются с cache
12) В файле info.csv найти все строки, которые содержат слово Company4
13) В директории text_processing создать файл products с содержимым
```
Handle:Title:SKU:Location:On hand:Available:Count
product-1:Product A:PROD-A:Warehouse A:100
product-1:Product A:PROD-A:Warehouse A:50
product-2:Product B:PROD-B:Warehouse B:200
product-2:Product B:PROD-B:Warehouse B:150
product-3:Product C:PROD-C:Warehouse C:300
product-4:Product D:PROD-D:Warehouse A:400
product-4:Product D:PROD-D:Warehouse A:250
product-5:Product E:PROD-E:Warehouse B:500
product-5:Product E:PROD-E:Warehouse B:300
product-6:Product F:PROD-F:Warehouse C:600
product-6:Product F:PROD-F:Warehouse C:400
```
14) С помощью grep найти в файле products все строки, содержащие слово PROD-C
15) С помощью grep найти в файле products все строки, содержащие слово product-3 и вывести для них последний столбец
16) С помощью grep найти в файле products все строки, у которых столбец Available равен C и для них вывести первый и последний столбец
17) В директории text_processing создать файл hosts с содержимым
```
hostname,interval,timestamp,%user,%system,%memory
sel-srv1,600,2023-10-08 00:00:01 UTC,30.01,20.77,96.21
sel-srv1,600,2023-10-08 00:05:01 UTC,40.07,13.00,84.55
sel-srv1,600,2023-10-08 00:10:01 UTC,5.00,90.55,89.23
sel-srv2,600,2023-10-09 00:15:01 UTC,25.01,15.77,92.21
sel-srv3,600,2023-10-09 00:20:01 UTC,35.07,10.00,80.55
sel-srv3,600,2023-10-09 00:25:01 UTC,10.00,85.55,88.23
sel-srv2,600,2023-10-09 00:30:01 UTC,20.01,25.77,95.21
sel-srv2,600,2023-10-09 00:35:01 UTC,45.07,12.00,82.55
sel-srv3,600,2023-10-09 00:40:01 UTC,15.00,80.55,87.23
```
18) С помощью grep найти в файле hosts строки, содержащие sel-srv2 и вывести 3 столбец
19) С помощью grep найти в файле hosts строки, содержащие дату 2023-10-08
20)  В директории text_processing создать файл inventory с содержимым
```
[Compute1]
IP_Address = 192.168.1.100
Location = Datacenter A
Service_Name = Web Server

[Compute2]
IP_Address = 192.168.1.101
Location = Datacenter B
Service_Name = Database Server

[Compute3]
IP_Address = 192.168.1.102
Location = Datacenter C
Service_Name = Application Server

[Compute4]
IP_Address = 192.168.1.103
Location = Datacenter A
Service_Name = File Server

[Compute5]
IP_Address = 192.168.1.104
Location = Datacenter B
Service_Name = Mail Server
```
21) С помощью grep в файле inventory найти все хосты, которые относятся к Datacenter B
22) С помощью grep в файле inventory найти все хосты, которые относятся к Datacenter C и вывести только их ip
23) Отфильровать вывод команды lscpu так, чтобы получить значение CPU MHz
24) Отфильровать вывод команды lscpu так, чтобы получить значение Hypervisor vendor
25) Из файла /proc/meminfo получить все строки. относящиеся к HugePages
26) Отфильтровать вывод команды lsblk так, чтобы получить все разделы (раздел это та строка, где 6 поле имеет значение part)
27) Для полученных в предыдущем задании разделов вывести их имена
28) С помощью awk вывести из файла /etc/passwd имена всех пользователей (первое поле)
29) С помощью awk вывести из файла /etc/passwd последнее поле
30) Отфильтровать вывод команды free -h так, чтобы получить размер Mem
31) В директории text_processing создать файл logs с содержимым
```
# Cron logs
Oct 20 06:24:01 server1 CRON[1349677]: (user1) CMD (   /usr/bin/python3 /home/user1/update.py)
Oct 20 06:25:01 server3 CRON[1349678]: (user2) CMD (   /usr/bin/python3 /home/user2/report.py)
Oct 20 06:26:01 server2 CRON[1349679]: (root) CMD (   /usr/bin/cleanup.sh)
Oct 20 06:27:01 server3 CRON[1349680]: (user3) CMD (   /usr/bin/backup.sh)
Oct 20 06:28:01 server1 CRON[1349681]: (user4) CMD (   /usr/bin/monitor.sh)

# Error logs
Oct 20 06:30:00 server1 sshd[12345]: Failed password for invalid user admin from 192.168.0.10 port 22 ssh2
Oct 20 06:31:00 server3 sshd[12346]: Failed password for invalid user guest from 192.168.0.11 port 22 ssh2
Oct 20 06:32:00 server1 sshd[12347]: Accepted password for user2 from 192.168.0.12 port 22 ssh2
Oct 20 06:33:00 server1 sshd[12348]: Failed password for invalid user test from 192.168.0.13 port 22 ssh2

# Warning logs
Oct 20 06:35:00 server1 kernel: [123456] Warning! CPU temperature is high.
Oct 21 09:10:00 server2 kernel: [123458] Warning! High CPU usage detected on process ID 5678.
Oct 21 09:11:00 server2 systemd[1]: Warning! Service myservice.service is taking too long to start.
Oct 21 09:12:00 server2 sshd[23461]: Warning! Multiple failed login attempts from 192.168.0.25.
Oct 21 09:13:00 server2 application[34571]: Warning! Disk space on /home is below 10% remaining.

# Info logs
Oct 21 09:02:00 server2 application[34569]: INFO User1 logged in successfully.
Oct 21 09:03:00 server2 application[34570]: INFO User3 logged out.
Oct 21 09:14:00 server2 application[34572]: INFO User4 logged in successfully from 192.168.0.26.
Oct 21 09:15:00 server2 application[34573]: INFO Backup completed successfully at /backup/user4_backup.tar.gz.
Oct 21 09:16:00 server2 systemd[1]: INFO Service myservice.service started successfully.
Oct 21 09:17:00 server2 sshd[23462]: INFO User1 logged out from session on terminal pts/0.
```
32) В файле logs.txt найти все записи, которые содержат application
33) В файле logs найти записи о запусках cron на сервере server3 и вывести команду, которая запускалась (это то, что в скобках в конце)

<img width="928" alt="image" src="https://github.com/user-attachments/assets/c61ff7c3-5346-45ff-a45e-c6511dde87a1">

34) В файле logs найти запись о сервисе myservice
35) В файле logs найти все записи, содержащие ssh и вывести для них название сервера (третье поле)

<img width="714" alt="image" src="https://github.com/user-attachments/assets/b13e56a0-1b74-438f-b910-55b9d4e1e4fa">

36) В файле logs найти все записи, содержащие kernel и вывести для них шестое поле
37) В файле logs найти все записи, содержащие "Failed password" и вывести только ip

<img width="699" alt="image" src="https://github.com/user-attachments/assets/da09364f-353d-4bd5-8563-423402547b1b">

38) В файле logs.txt найти записи, содержащие "Accepted password" и вывести имя пользователя и ip

<img width="688" alt="image" src="https://github.com/user-attachments/assets/1d36804e-31b3-4257-9b1d-97c0130a3acc">

39) В файле logs.txt найти записи, содержащие "Disk space" и вывести название сервера
40) Из файла /etc/os-release получить версию установленного Linux
# Пользователи и права доступа
1) Создать пользователей user_{1,2,3,4,5}
2) Вывести из файла /etc/passwd только имена созданных пользователей (grep)
3) Добавить группы workers; teachers; students
4) Вывести из файла /etc/group только названия добавленных групп
5) Пользователей user_1 и user_2 добавить в группу workers
6) Пользователей user_3, user_4, user_5 добавить в группу students
7) Создать пользователя mentor3 и добавить в группу teachers
8) Вывести на экран состав групп workers; teachers; students
9) Задать пароли для всех пользователей
10) С помощью команды id вывести информацию о пользователе mentor3 и вывести только список его групп
11) Создать группы developers, designers, managers и admins
12) Создать пользователей jdoe, asmith, mjackson, kchen, rgarcia
13) Добавить пользователей
- mjackson в группу admins
- jdoe, kchen, rgarcia в группу developers
- asmith - в группу designers
14) Вывести из файла /etc/passwd только имена созданных пользователей
15) Вывести из файла /etc/group названия и состав добавленных групп
16) Задать пользователям пароли
17) Добавить пользователя asmith в группу managers
18) С помощью команды id получить информацию о пользователе asmith и вывести его первичную группу
19) Выполнить команду ```sudo getent shadow``` и из ее вывода получить имена добавленных в п2 пользователей и хеши их паролей
   В домашней директории создать директорию magento
20) В директории magento создать директории media, code и styles
21) В директории code создать файл index.php с содержимым
```
<?php
phpinfo();
?>
```
22) В директории styles создать файл main.css с содержимым
```
h1 {
    color: #333; /* Цвет текста */
    text-align: center; /* Выравнивание по центру */
}
```
23) В директории magento создать файл index.html с содержимым
```
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>E-commerce page</title>
    <link rel="stylesheet" href="styles.css"> <!-- Подключаем CSS -->
</head>
<body>
    <header>
        <h1>Welcome!</h1>
        <h2>e-commerce site</h2>
    </header>
```
24) Сделать владельцем файла index.html пользователя mjackson, а группой владельцев - группу developers
25) Сделать владельцем файла styles/main.css пользователя asmith, а группой владельцев - группу designers
26) Сделать владельцем файла code/index.php пользователя rgarcia, а группой владельцев - группу admins
# Установка ПО
1) По инструкции https://docs.docker.com/engine/install/debian/#install-using-the-repository установить докер
2) Установить git, gnupg2 и lsb-release
3) Выполнить
```
git clone https://github.com/AnastasiyaGapochkina01/06_home_work.git
cd 06_home_work/
sudo docker compose up -d --build
```
4) Выполнить
```
docker exec -it old-debian bash
```
с этого момента ты в docker-контейнере и все действия делаем там
5) Перейти в директорию /usr/src/php. Там лежит исходный код php версии 5.3
6) Собрать php версии 5.3 из исходников и установить в систему
7) Установить gnupg2 и lsb-release
8) Скачать пакет
```
wget http://ftp.de.debian.org/debian/pool/main/m/memstat/memstat_1.1+b1_amd64.deb
```
и установить его
9) Установить percona в контейнер
10) После того как закончил - выполнить
```
exit
sudo docker compose down -v
```
# Процессы
1) Выполнить команду ```top &> /dev/null &```
2) С помощью ps найти процесс top
3) В директории /proc найти каталог, который соответствует найденному выше процессу top
4) Убить процесс top
5) В домашней директории диреткорию servers и в ней создать файл web_server с содержимым
```
#!/bin/bash
LOG_FILE="$HOME/web_server.log"
log_levels=("ERROR" "INFO" "WARNING" "DEBUG")
methods=("GET" "POST" "PUT" "PATCH" "OPTIONS" "DELETE")
echo "Starting web-server on $(hostname)" >> $LOG_FILE
while true
do
  sleep 5
  random_method=${methods[$RANDOM % ${#methods[@]}]}
  random_level=${log_levels[$RANDOM % ${#log_levels[@]}]}
  echo "$(date +"%Y-%d-%m [%H:%M:%S]") $random_level $random_method" >> $LOG_FILE
  sleep 5
done
```
6) Сделать файл web_server исполняемым для всех
7) Выполнить команду ```./web_server &> /dev/null &```
8) Найти id процесса web_server
9) В домашней директории найти файл web_server.log и посмотреть его содержимое
10) В директории /proc найти каталог, который соответствует найденному выше процессу web_server
11) Запустить top и найти в нем процесс web_server. Сколько CPU и MEM он потребляет?
12) Приостановить процесс web_server (поставить на паузу, а не убить)
13) Вернуть из паузы процесс web_server
14) Убить процесс web_server
15) В директории servers создать файл simple-server с содержимым
```
#!/bin/bash
LOG_FILE="simple_server.log"

log() {
    echo "$(date '+%Y-%m-%d %H:%M:%S') - $1" >> "$LOG_FILE"
}

if command -v nc >/dev/null 2>&1; then
  log "Skipping..."
else
  if sudo apt-get update && sudo apt-get install -y netcat; then
    log "Succees"
  else
    log "Error when install netcat"
  fi
fi

PORT=8082
while :; do
  { echo -ne "HTTP/1.1 200 OK\r\nContent-Length: $(echo -n "Hello, World!")\r\n\r\nHello, World!"; } | nc -l -p "$PORT" >> simple_server.log 2>&1
done
```
16) Выполнить команду ```./simple-server &> /dev/null &```
17) Найти id процесса simple-server
18) Выполнить команду curl 127.0.0.1:8082
19) Проверить, появился ли в директории servers файл simple_server.log, посмотреть его содержимое
20) В директории /proc найти каталог, который соответствует найденному выше процессу simple-server
21) Запустить top и найти в нем процесс simple-server
22) Приостановить процесс simple-server
23) Вернуть из паузы процесс simple-server
24) Убить процесс simple-server
# Работа с systemd
1) Установить на ВМ php
2) В директории /opt создать папку rot13
3) В директории /opt/rot13 создать файл с именем rot13-server.php с кодом
```
<?php
$sock = socket_create(AF_INET, SOCK_DGRAM, SOL_UDP);
socket_bind($sock, '0.0.0.0', 10000);
for (;;) {
  socket_recvfrom($sock, $message, 1024, 0, $ip, $port);
  $reply = str_rot13($message);
  socket_sendto($sock, $reply, strlen($reply), 0, $ip, $port);
}
```
4) Запустить сервер командой php rot13-server.php и проверить что сервер работает: выполнить nc -u 127.0.0.1 10000 и ввести Hello World
5) Написать юнит-файл для запуска rot13-server.php как сервиса
6) Установить nginx, если он еще не установлен
7) Посмотреть статус демона nginx
8) Остановить nginx
9) Запустить nginx
10) Убрать nginx из автозагрузки
11) Вернуть nginx в автозагрузку
12) "Замаскировать" nginx, попробовать перезапустить/остановить/запустить nginx; снять с nginx "маскировку"
13) Установить redis ([install-redis-on-linux](https://redis.io/docs/latest/operate/oss_and_stack/install/install-redis/install-redis-on-linux/)) - ссылка доступна под VPN
14) Посмотреть статус демона redis
15) Запустить второй экземпляр демона redis, написав systemd unit
# Работа с дисками и LVM
1) Добавить к ВМ дополнительный диск
2) Установить postgresql, убедиться что он запущен
3) Выяснить, где находится директория с данными
```
sudo su - postgres
psql
# SHOW data_directory;
```
4) Вынести эту директорию на дополнительный диск без потери данных (обязательно рестартануть сервис и проверить что БД на месте)
5) Установить mongodb
6) Выяснить, где находится директория с данными
```grep -i dbPath /etc/mongod.conf```
7) Подключить еще один дополнительный диск к ВМ
8) Сделать из нового диска PV, из PV - VG
9) Создать Logical Volume mongo-data и вынести директорию из п6 на него
10) Убедиться, что все прошло корректно
# bash-скрипты
1) Написать скрипт, который будет собирать информацию о системе и выводить ее в табличном виде:
- версия ОС
- количество ядер cpu
- размер оперативной памяти
- размер ФС, смонтированной в /
2) Написать скрипт, который будет создавать 5 пользователей:
- имена создаются по шаблону user_N_N+1, где N=2
- после создания генерируются случайные пароли и назначаются пользователям
3) Написать скрипт для автоматической установки nginx+php+mysql. Скрипт должен проверять, установилось ли ПО (хотя бы запросом версии)
4) Написать скрипт осуществляющий вывод меню, состоящего из следующих пунктов (и вывод соответствующей информации в зависимости от выбранного пункта меню. Процесс повторять до тех пор, пока не будет выбран пункт меню «выход»):
- текущий пользователь,
- объем используемой памяти,
- объем дискового пространства,
- список запущенных процессов,
- системные дата и время,
- время запуска системы
- выход
