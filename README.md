# KITTYGRAM

### https://my-kittygram.myvnc.com/

[![Main Kittygram workflow](https://github.com/EvstratovRG/kittygram_final/actions/workflows/main.yml/badge.svg)](https://github.com/EvstratovRG/kittygram_final/actions/workflows/main.yml)

## Технологии:
- backend: python3.9, Django Rest Framework, postgresql:13.10
- frontend: javascript, node:18
Так же в проекте использовалась контейнеризация Docker.
В качестве обратного прокси-сервера использовался Nginx.

## Описание проекта:
- Лучший способ поделиться с другими кошатниками фото и достижениями своего питомца.

## Как запустить проект:
- Для начала необходимо установить Docker, инструкции соотвествующие вашей ОС ищите на официальном сайте https://www.docker.com/

- следом, клонируйте репозиторий: git clone https://github.com/EvstratovRG/kittygram_final.git
- затем перейдите в клонированный репозиторий: cd kittygram_final/
- далее требуется создать файл переменных окружения: touch .env

- Для работы проекта, необходимо задать переменные значения. Откройте файл .env и заполните данными.

DJANGO_KEY=<секретный ключ джанго>
POSTGRES_DB=<Желаемое_имя_базы_данных>
POSTGRES_USER=<Желаемое_имя_пользователя_базы_данных>
POSTGRES_PASSWORD=<Желаемый_пароль_пользователя_базы_данных>
DB_HOST=db
DB_PORT=5432
ALLOWED_HOSTS=<перечень доступных хостов - ЧЕРЕЗ ПРОБЕЛ!!! localhost 127.0.0.1 и тд.>

- следом, требуется запустить программу докер и в командной строке выполнить следующие команды.

sudo docker compose -f docker-compose.production.yml pull
sudo docker compose -f docker-compose.production.yml down
sudo docker compose -f docker-compose.production.yml up -d

- перейдите в другой терминал и выполните эти действия в той же директории
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collect_static/. /static_backend/static/

- создайте суперюзера и проект готов к работе!

sudo docker compose -f docker-compose.production.yml exec backend python manage.py createsuperuser



## Автор: Евстратов Р.Г.