1) Установить на ВМ mariadb. Задать пароль пользователю root после установки
2) Создать бд bookstore. В БД bookstore создать таблички
- books

|book_id|author_id|title|author|price|ISBN|
|:---:|:---:|:---:|:---:|:---:|:---:|
|1|2|Underground|H.Murakami|599|978-3-16-148239-7|
|2|1|Ulysses|J.Joyce|490|978-3-12-987654-3|
|3|3|The Trial|F.Kafka|350|978-5-17-123456-1|

- authors

|author_id|name|
|:---:|:---:|
|1|J.Joyce|
|2|H.Murakami|
|3|F.Kafka|

3) Создать пользователя bookuser и дать ему полные права на бд bookstore
4) Написать скрипт для создания бэкапов БД
5) Удалить БД bookstore и восстановить ее из бэкапа
6) Запустить phpmyadmin с помощью nginx
