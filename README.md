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


## MySQL with Docker

```
docker run --name mysql57 -p 3306:3306 -e MYSQL_ROOT_PASSWORD=abcd -d mysql/mysql-server
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

-- If we have already user id, password and database passed through environmental variables while running docker run,

```
docker exec -it mysql57 bash
```

```
mysql -uroot -p
```

```
connect myDB
```


```
docker run --name mysql -p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=abcd \
-e MYSQL_USER=docker_mysql \
-e MYSQL_PASSWORD=docker_mysql \
-e MYSQL_DATABASE=docker_mysql_db \
-d mysql/mysql-server:5.7
```

## Create a dedicated network to connect javaapp and mysql

- create network
  
```docker network create app-network ```

```docker network ls ```

### connect app-db container to app-network

```docker run --name app-db -p 3306:3306 --env MYSQL_ROOT_PASSWORD=password --env MYSQL_DATABASE=myDB -d mysql:latest```

``` docker network connect app-network app-db```




- modify application code to use container name in database url

``` <propery name="javax.persistence.jdbc.url" value="jdbc:mysql://app-db/myDB" /> ```

- Build the java application and Image
  
``` docker build -t myjavaapp . ```
```docker run --name myjavaapp-container -d -p 8080:8080 --network=app-network  myjavaapp```

(In a single command we can specify network as well, app-db is a container name for mysql)

### Example App
```
https://github.com/vravipati9/docker-java-web-app
```


- Table Example

| Plugin | README |
| ------ | ------ |
| test | test |
| test | test |
