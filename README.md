If you want to read in English, please scroll down.

# このリポジトリについての説明
このリポジトリはDjangoのプロジェクトをDockerを使って立ち上げるためのベースです。  
公式ではPostgreSQLを使っていますが、ここではMariaDBを使って構築しています。  
時々更新します。  
  
## 設定の進めかた
### リポジトリのクローン
以下のコマンドでリポジトリをクローンしてください
```shell
$ git clone https://github.com/kaedemalu/django-maria.git # use https
```
### データベースの初期設定
以下のコマンドを打ってDBの設定の初期設定を行います。
```shell
$ docker-compose up db -d
$ docker-compose run web python3 ./manage.py makemigrations
$ docker-compose run web python3 ./manage.py migrate
```
はじめにDBのコンテナのみ立ち上げる必要があるので、最初のコマンドが必要になります。  
次に、マイグレーションの作成のために2番目のこマントを打ちます。  
3つめのコマンドで、マイグレーションの実行ができます。  
### webコンテナの起動からページの表示まで
webコンテナを起動
```shell
$ docker-compose up web -d
```
http://0.0.0.0:8000  
上記にアクセスし、ページが表示されているか確認する。  

### root権限のユーザーの作成
以下のコマンドを実行し、rootユーザーを作成します。   
```shell
$ docker-compose run web python3 ./manage.py createsuperuser
```
root権限のユーザー名、メールアドレス、パスワードを聞かれます。  
メールアドレスはブランクでも進めます。  
パスワードについては短くても作成できますが(ex: pass)、怒られます。  
http://0.0.0.0:8000/admin  
上記にアクセスし、設定したユーザー名、パスワードを入力しアクセスできるか確認する。  

# Description about this repository.
This repository is a base of Django project that use with Docker.  
Official tutorial uses PostgreSQL but this repository uses MariaDB.  
  
## Settings
### Clone this repository
Clone this repository that use following command.  
```shell
$ git clone https://github.com/kaedemalu/django-maria.git # use https
```
### Initial settings of Database  
Type following commnands.  
```shell
$ docker-compose up db -d
$ docker-compose run web python3 ./manage.py makemigrations
$ docker-compose run web python3 ./manage.py migrate
```
### Start up web container and display page.
```shell
$ docker-compose up web -d
```
Access to following URL and check a page.  
http:0.0.0.0:8000  
  
### Make root user.
Type following command and setup root user name and password.  
```shell
$ docker-compose run web python3 ./manage.py createsuperuser
```
Access to following URL and type root user name and password.  
http:0.0.0.0:8000/admin  
