# Api_Yatube
---
api_yatube - это API социальной сети Yatube.
## Описание
---
- С его помощью можно просматривать посты, удалять их, создавать и  изменять.
- Подписка и отписка от авторизованного пользователя.
- Возможность комментировать посты.

Автор: Андрей Игнатев
## Установка
---
Клонировать репозиторий и перейти в него в командной строке:
```sh
git clone https://github.com/iwanttobe00/api_yatube.git
```
```sh
cd api_yatube
```
Cоздать и активировать виртуальное окружение:
```sh
python3 -m venv env
```
```sh
# для OS Lunix и MacOS
source venv/bin/activate
# для OS Windows
source venv/Scripts/activate
```
Установить зависимости из файла requirements.txt:
```sh
python -m pip install --upgrade pip
```
```sh
pip install -r requirements.txt
```
Выполнить миграции:
```sh
cd yatube_api
python manage.py makemigrations
python manage.py migrate
```
Запустить проект:
```sh
python manage.py runserver
```
## Примеры
---
```sh
ПО для тестирования API:
https://www.postman.com/
```
Сначала надо получить токен, чтобы создавать посты, комментировать, подписываться на других авторов.
Для этого нужно отправить POST-запрос на адрес ```api/v1/jwt/create/``` и передать 2 поля в ```data```:
1. ```username:``` ```String```
2. ```password:``` ```String``` 

В  ```Headers``` указать ```Authorization```:```Bearer <токен>```.
#### Создать пост
Отправить POST-запрос на адрес ```api/v1/posts/```
```sh
{
  "text": "string."
}
```
##### "text"- обязательное поле для создания поста
Ответ который получили:
```sh
{
"id": 0,
"author": "string",
"text": "string.",
"pub_date": "2019-08-24T14:15:22Z",
"image": "string",
"group": 0
}
```
#### Комментирование поста
Отправить POST-запрос на адрес ```api/v1/posts/{post_id}/comments/```
```sh
{
"text": "string"
}
```
##### "text"- обязательное поле для комментирования поста
Ответ который получили:
```sh
{
"id": 0,
"author": "string",
"text": "string",
"created": "2019-08-24T14:15:22Z",
"post": 0
}
```
