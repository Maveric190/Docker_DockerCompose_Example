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
Коментарий. К сожалению не получилось автоматизировать запуск баш скрипта, образ контейнера не хочет пересобираться :
   docker build -t humble-desktop-prepaired                  
   ERROR: "docker buildx build" requires exactly 1 argument.
   See 'docker buildx build --help'.

   Usage:  docker buildx build [OPTIONS] PATH | URL | -

   Start a build
7. Пишу файл docker-compose.yml
8. Собираю и запускаю образ контейнера:
   docker-compose up
   Результат выполнения команды на скриншоте Снимок экрана от 2024-02-10 22-16-06_2
   Здесь удалось автоматизировать сервис локального времени и запуск скрипта, но: !
   (1. не подключаестся том докер myvolume, пришлось указывать локальную папку со скриптом. 2 Текущее время не выводится на экран терминала (но выводится при закрытии контейнера командой docker-compose down)).
