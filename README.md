# docker-laravel-mysql

Laravel5.8 & MySQL8.0のDocker開発環境

## Description
Dockerを利用した Laravel Echo Server の開発環境
- PHP7.3
- MySQL8.0
- nginx
- composer
- redis
- node
- php-worker


## Usage
### Git clone
```
$ git clone https://github.com/nakanakamu0828/docker-laravel-mysql
$ cd docker-laravel-mysql
```

### Docker compose build
```
$ docker-compose up -d --build
```

### Git clone project
```
$ git clone [github repogitory url] src
```

### Composer install
```
$ docker-compose run composer install
```

### Setup Laravel
```
$ docker-compose exec app sh
$ cp -p .env.example .env
$ sed -i -e "s/DB_HOST=.*/DB_HOST=db/" .env
$ sed -i -e "s/REDIS_HOST=.*/REDIS_HOST=redis/" .env
$ php artisan key:generate
```

### Setup Mail
```
$ docker-compose exec app sh
$ sed -i -e "s/MAIL_HOST=.*/MAIL_HOST=mail/" .env
$ sed -i -e "s/MAIL_PORT=.*/MAIL_PORT=1025/" .env

$ php artisan tinker
Mail::raw('test mail',function($message){$message->to('test@example.com')->subject('test');});
```
http://localhost:3354/


### Migration
```
$ docker-compose exec app sh
$ php artisan migrate
```

### Setup Frontend
#### NPM
```
$ docker-compose run node npm install
$ docker-compose run node npm run dev
```

#### yarn
```
$ docker-compose run node yarn install
$ docker-compose run node yarn run dev
```

http://localhost:8880/
