1) Запустить контейнер nginx:
- создать и прокинуть внутрь контейнера папку app (монтировать в /usr/share/nginx/html)
- в папке app создать файл index.html с таким содержимым
```
<Html>
<Head>
<title>
Example of make a text B,I,U
</title>
</Head>
<Body>
<b> [This text is Bold......] </b>
<I> [This text is Italic......] </I>
<U> [This text is Underline......] </U>
</Body>
</Html>
```
- вывесить порт 80 из контейнера на порт хоста 8090
при выполнении curl на ip:port должна отдаваться созданная в app страничка
2) Запустить контейнер с mongodb:
- задать переменную ME\_CONFIG\_MONGODB\_ADMINUSERNAME со значением admin
- задать переменную ME\_CONFIG\_MONGODB\_ADMINPASSWORD со значением adminpassword
- создать директорию mongo\_data и смонитировать ее внутрь контейнера в /data/db
- вывесить дефолтный порт монги на хост, проверить с помощью nc
3) Запустить контейнер с postgres 9:
- задать переменную POSTGRES\_PASSWORD со значением passwd
- создать директорию pg\_data и прокинуть ее в контейнер по пути /var/lib/postgresql/data
4) Для всех контейнеров, запущенных в п1-3 выяснить с помощью docker inspect выяснить
- ip-адрес
- volumes
- image
5) Запустить с помощью docker compose mongodb и mongo-express
6) Запустить с помощью docker compose gitea
7) Запустить с помощью docker compose portainer
8) Запустить с помощью docker compose prometheus и grafana
9) Запустить wordpress с помощью docker compose
10) Запустить с помощью docker compose nextloud
11) Запустить в docker приложение https://github.com/AnastasiyaGapochkina01/flask-redis/tree/main
12) Запустить в docker приложение https://github.com/AnastasiyaGapochkina01/front-back-app/tree/main
13) Написать самостоятельно любое элементарное API на go/python/nodejs и запаковать его в docker
