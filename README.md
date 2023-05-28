# Dockerでの Laravel + MySQL + Nginx + phpMyAdmin 環境構築
このプロジェクトは Docker を用いて Laravel, MySQL, Nginx, phpMyAdmin の環境を構築します。
## ファイル構造
```
/project
├── docker
│ ├── mysql
│ │ ├── my.cnf
│ ├── nginx
│ │ ├── default.conf
│ └── php
│ ├── Dockerfile
├── docker-compose.yml
└── src
```
## セットアップ手順
1. Docker と Docker Compose がインストールされていることを確認してください。
2. リポジトリをクローンまたはダウンロードします。
3. プロジェクトディレクトリに移動します。
```
cd docker_laravel_mysql_nginx_phpmyadmin
```
4. .env.exampleをコピーして、.envのファイルを作り編集する
```
# MySQL settings
DB_ROOT_PASSWORD=root_password       # root_passwordを変更する
DB_DATABASE=laravel                  # laravelを変更する
DB_USERNAME=my_user                  # my_userを変更する
DB_PASSWORD=my_password              # my_passwordを変更する

# phpMyAdmin settings
PMA_HOST=mysql
PMA_USER=${DB_USERNAME}
PMA_PASSWORD=${DB_PASSWORD}
```
5. Docker コンテナをビルドし、バックグラウンドで実行します。
```
docker-compose up -d --build
```
6. PHP コンテナ内で Laravel をインストールします。
```
docker-compose exec php composer create-project --prefer-dist laravel/laravel .
```

## ブラウザでのアクセス
1. `http://localhost:8080` にアクセスして Laravel のウェルカムページが表示されることを確認します。
2. `http://localhost:8081` にアクセスして phpMyAdmin のページが表示されることを確認します。

