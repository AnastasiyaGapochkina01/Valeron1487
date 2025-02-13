1) Создать директорию ansible-collection. В ansible-collection создать директорию files
2) В files создать файл nginx.conf, в который записать строку
```Hello from nginx```
3) Написать плейбук, который
- скопирует файл files/nginx.conf в /opt
- создаст пользователя nginx_user
4) Написать плейбук, который установит nginx
5) Написать плейбук, который установит php8.0
6) Написать роль для установки hashicorp vault
7) Написать роль для установки и настройки zabbix-agent. В /etc/zabbix/zabbix_agentd.conf надо:
- изменить поле Hostname на понятное имя машины
- добавить поле HostMetadataItem=system.uname
- убедиться что агент запущен
8) Написать роль для установки и настройки nginx, которая будет
- устанавливать nginx
- создавать в /var/www папку website
- копировать в нее папку project (в папке project должен лежать репозиторий https://github.com/AnastasiyaGapochkina01/website)
- копировать в /etc/nginx/sites-available файл с конфигрурацией nginx (https://github.com/AnastasiyaGapochkina01/website/blob/main/nginx.conf)
- удалять файл /etc/nginx/sites-enabled/default
- делать симлинк /etc/nginx/sites-available/website.conf в /etc/nginx/sites-enabled/website.conf
- рестартовать nginx
9) Написать роль для установки composer (https://getcomposer.org/download/)
10) Написать роль для установки nodejs (сделать возможность выбора устанавливаемой версии с помощью переменной)
