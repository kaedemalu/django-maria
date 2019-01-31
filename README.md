# This project is.....
This project is a base of Django project that use with Docker and docker-compose

## 設定の進めかた
以下のコマンドを打ってDBの設定を進めていく
```
$ docker-compose up db -d
$ docker-compose run web python3 ./manage.py makemigrations
$ docker-compose run web python3 ./manage.py migrate
```
次にwebコンテナを起動
```
$ docker-compose up web -d
```
.
