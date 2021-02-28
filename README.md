# laravel-docker-environment
composer create-project --prefer-dist laravel/laravel をインストールする前までの構築


## install
``` git clone https://github.com/akiyoshi-takazwa/laravel-docker-environment.git ```

## introdution


### dockerの立ち上げ

``` docker-compose up -d --build ```

### laravel-project の作成
- ``` docker-compose exec php bash ```
- ``` composer create-project --prefer-dist laravel/laravel=好きなバージョン ```

### nginxのdefault.conf を下記に設定する

laravelは、プロジェクト名を入れる

```
server {
  listen 80;
    index index.php index.html;
    root /var/www/laravel/public/;

  location / {
    root /var/www/laravel/public;
    index  index.html index.php;
    try_files $uri $uri/ /index.php$query_string;
    }

```

### local環境の確認
http://localhost にアクセスしlaravelページが表示されるか確認


### databaseの確認

``` docker-compose exec php bash ```
``` php artisan migrate ```

### phpadmin とデータベースの確認を行う

http://localhost:8080 にアクセスし、phpmyadminが立ち上がりDB内に2つのテーブルが作成されているか確認


