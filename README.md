ОТЧЕТ по практической работе 5 курса "Linux для робототехников"
1. Создал bash скрипт example4.bash
2. Создал dockerfile (в данном случае взят докерфайл из видеоурока, он мне подходит).
3. Собрал образ контейнера командой docker build -t humble-desktop-prepaired
4. Запуск контейнера с подключением тома, в котором лежит скрипт example4.bash командой:
   docker run -it -v myvolume:/app/data humble-desktop-prepaired /bin/bash
5. Далее внутри контейнера синхронизирую время контейнера и запускаю скрипт:
   sudo unlink /etc/localtime
   sudo ln -s /usr/share/zoneinfo/Europe/Moscow /etc/localtime
   bash app/data/example4.bash
6. Результат выполнения скрипта на скриншоте "Снимок экрана от 2024-02-08 21-59-05_1"
