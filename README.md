# Docker
Для обновления версии redmine нужно всего лишь выполнить две команды

docker-compose build  
docker-compose restart

Если хочется ещё и отправки уведомлений на почту, то пишем файл configuration.yml

nano ~/docker/storage/configuration.yml 
с примерно таким содержимым. Настройки почты для каждого отдельного сервиса, будь то gmail, yandex или rambler свои

 production:
   email_delivery:
     delivery_method: :smtp
     smtp_settings:
       enable_starttls_auto: true
       address: "smtp.gmail.com"
       port: 587
       domain: "smtp.gmail.com"
       authentication: :plain
       user_name: "your_email@gmail.com"
       password: "password" 
В файл docker-compose.yml вставляем после строк с вынесенными вовне директориями следующую строку

- ./docker/storage/configuration.yml:/usr/src/redmine/config/configuration.yml
