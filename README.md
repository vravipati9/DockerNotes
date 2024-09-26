# DockerNotes


## To Build an Image
- go to Dockerfile location
```docker build -t myjavaapp . ```

## To Run container from Image

``` docker run -itd -p 8080:8080 --name myjavaapp-container myjavaapp ```
- myjavaapp-container is container name
- myjavapp is Image 

## Go to container terminal
```docker exec -it myjavaapp-container sh```

## To Remove the container after exit
``` docker run --rm -it dockerdemo-openjdk```
## To view logs by containername
```docker logs myjavaapp-container  ```



## Create Network
``` docker network create app-network ```

## list networks
``` docker network ls ```

```sh
127.0.0.1:8000
```

## MySQL with Docker

```
docker run --name mysql57 -p 3306:3306 -e MYSQL_ROOT_PASSWORD=abcd -d mysql/mysql-server
```

```
docker exec -it mysql57 bash
```

```
docker exec -it mysql57 bash
```

```
create user 'docker_mysql' identified by 'docker_mysql'
```

```
grant all on *.* to 'docker_mysql'@'%' identified by 'my-secret-pw';
```

```
flush privileges;
```

```
CREATE DATABASE docker_mysql_db CHARACTER SET utf8 COLLATE utf8_general_ci;
```

```
docker run --name mysql -p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=abcd \
-e MYSQL_USER=docker_mysql \
-e MYSQL_PASSWORD=docker_mysql \
-e MYSQL_DATABASE=docker_mysql_db \
-d mysql/mysql-server:5.7
```

## Create a dedicated network to connect javaapp with mysql

- create network
```docker network create app-network ```

```docker network ls ```

``` docker network connect app-network app-db```

## connect app-db container to app-network

```docker build -t my-web-app .```

-- In a single command we can specify network as well
```docker run --name app -d -p 8080:8080 --network=app-network  my-web-app```
app-db is a container name for mysql

- modify application code to use container name in database url
  
``` <propery name="javax.persistence.jdbc.url" value="jdbc:mysql://app-db/myDB" /> ```
- Build the java application and Image
``` docker build -t my-webapp . ```

``` docker run --name app -d -p 8080:8080 --network=app-network my-web-app ```

-- 

- Table Example

| Plugin | README |
| ------ | ------ |
| test | test |
| test | test |
