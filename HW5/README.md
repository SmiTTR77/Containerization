# Урок 5. Docker Compose и Docker Swarm

## Задание

### 1. Создать сервис, состоящий из 2 различных контейнеров

```
 1 - веб,
 2 - БД (compose)
```

### 2. Необходимо создать 3 сервиса в каждом окружении (dev, prod, lab) *

### 3. По итогу на каждой ноде должно быть по 2 работающих контейнера *

[**`Для тех кому интересно про Сфарм`**](https://github.com/Terekhov-A-S/Containerization-Seminar_5)

### 4. Выводы зафиксировать

```
* - Задание повышенной сложности. Не обязательно.
```

## Решение

```
sudo docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:8.0.31

```

```
sudo docker run --name myphp -d --link some-mysql:db -p 8081:80 phpmyadmin/phpmyadmin
```

![sudo docker run](https://github.com/SmiTTR77/Containerization/blob/main/HW5/img/1.png)

Открываем через браузер на виртуальной машине:

![localhost:8081](https://github.com/SmiTTR77/Containerization/blob/main/HW5/img/2.png)

![localhost:8081](https://github.com/SmiTTR77/Containerization/blob/main/HW5/img/3.png)

```
vi docker-compose.yml
 или
nano docker-compose.yml
```

```
version: '3.1'

services:
  db:
    image: mariadb:10.10.2
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: 12345
        
  adminer:
    image: adminer:4.8.1
    restart: always
    ports:
      - 6080:8080

```

![docker-compose.yml](https://github.com/SmiTTR77/Containerization/blob/main/HW5/img/4.png)

```
sudo docker-compose up -d
```

```
docker ps -a
```

![udo docker-compose up -d](https://github.com/SmiTTR77/Containerization/blob/main/HW5/img/5.png)

Открываем через браузер на виртуальной машине:

![localhost:6080](https://github.com/SmiTTR77/Containerization/blob/main/HW5/img/6.png)

![localhost:6080](https://github.com/SmiTTR77/Containerization/blob/main/HW5/img/7.png)
