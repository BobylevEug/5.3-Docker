# 5.3-Docker

## 1. Посмотрите на сценарий ниже и ответьте на вопрос: "Подходит ли в этом сценарии использование докера? Или лучше подойдет виртуальная машина, физическая машина? Или возможны разные варианты?"

- Высоконагруженное монолитное java веб-приложение;
  Да. В случае с ФМ или ВМ, при необходимости срочной масштабируемости придется запускать, создавать, переделывать. В то время, как с контейнером просто запустить еще несколько.
- Go-микросервис для генерации отчетов;
  На виртуалке достаточно (чаще всего уже завернуты)
- Nodejs веб-приложение;
  Лучше контейнер, большое количество разного рода зависимостей.
- Мобильное приложение c версиями для Android и iOS;
  Необходима эмуляция для тестирования - ВМ или ФМ.
- База данных postgresql используемая, как кэш;
  Если бд на долгосрочной основе то их на ФМ, как кэш проще в ВМ.
- Шина данных на базе Apache Kafka;
  Да, в случае с менеджерами очередей можно контейнер.
- Очередь для Logstash на базе Redis;
  Из-за возможной необходимой максимальной производительности лучше на ФМ (много данных хранит в опер памяти).
- Elastic stack для реализации логирования продуктивного веб-приложения - три ноды elasticsearch, два logstash и две ноды kibana;
  На ФМ
- Мониторинг-стек на базе prometheus и grafana;
  Контейнер.
- Mongodb, как основное хранилище данных для java-приложения;
  БД лучше на железе.
- Jenkins-сервер.
  Контейнер.
  
## 2. Опубликуйте созданный форк в своем репозитории и предоставьте ответ в виде ссылки на докерхаб-репо.

Команды:
- Запуск docker run -dit --name my-apache-app -p 8080:80 -v "$PWD":/usr/local/apache2/htdocs/ httpd:2.4
- создан файл на хосте index.html
- копирование файла с хоста в контейнер docker cp /home/kali/Documents/apache/index.html thirsty_chandrasekhar:/usr/local/apache2/htdocs
- проверка docker exec -it thirsty_chandrasekhar bash
