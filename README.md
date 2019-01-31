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
次に、マイグレーションの作成のために2番目のこマントを打ちます
3つめのコマンドで、マイグレーションの実行ができます。
### webコンテナの起動からページの表示まで
webコンテナを起動
```shell
$ docker-compose up web -d
```
http://0.0.0.0:8000にアクセスし、ページが表示されているか確認する

### root権限のユーザーの作成
以下のコマンドを実行し、rootユーザーを作成します
```shell
$ docker-compose run web python3 ./manage.py createsuperuser
```
root権限のユーザー名、メールアドレス、パスワードを聞かれます
メールアドレスはブランクでも進めます。
パスワードについては短くても作成できますが(ex: pass)、怒られます
