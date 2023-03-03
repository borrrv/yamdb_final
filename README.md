# yamdb_final
yamdb_final

![yamdb_workflow](https://github.com/borrrv/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

## Описание
API YaMDb -  это интерфейс, который позволяет пользователям получать и публиковать отзывы на произведения. В проекте хранятся отзывы на произведения , а также комментарии к отзывам. Все произведения делятся на категории , также каждому произведению может быть присвоен один или несколько жанров. У каждого произведения присутствует рейтинг, который строится по средней оценке всех отзывов на данное произведение. 

## Пример сайта
http://localhost:8000/redoc/

## Запуск проекта
- Делаем форк репозитория
- Клонируем репозиорий
```
git clone git@github.com:<ваш_логин>/yamdb_final.git
```
- Заходим на удаленный сервер и подготавливаем его(инструкци для Ubuntu 20.04)
- Устанавливаем docker и docker-compose
```
sudo apt update
sudo apt install docker.io
sudo apt install docker-compose
sudo systemctl start docker
```
- Добавляем в Secrets GitHub Actions переменные окружения:
```
AUTHORIZED_KEYS
DB_ENGINE
DB_HOST
DB_NAME
DB_PORT
DOCKER_PASSWORD
DOCKER_USERNAME
HOST
PASSPHRASE
POSTGRES_PASSWORD
POSTGRES_USER
SSH_KEY
TELEGRAM_TO
TELEGRAM_TOKEN
USER
```
- Поднимаем контейнеры
```
sudo docker-compose up -d --build 
```
- Выполняем миграции
```
sudo docker-compose exec web python manage.py migrate
```
- Создаем суперпользователя
```
docker-compose exec web python manage.py createsuperuser 
```
- Собираем статику
```
docker-compose exec web python manage.py collectstatic --no-input 
```
- Остановить контейнеры
```
docker-compose down -v 
```
## Стек
- Python 3.9
- Django 2.2.16
- DRF 3.12.4
- PostgreSQL
- Docker-compose
- Nginx
- DockerHub
