# DockerNotes


## To Build an Image
- go to Dockerfile location
```docker build -t myjavaapp . ```

## To Run container from Image

``` docker run -itd -p 8080:8080 --name myjavaapp-container myjavaapp ```
- myjavaapp-container is container name
- myjavapp is Image 

## Go to container terminal
```exec myjavaapp-container```

## To Remove the container after exit
``` docker run --rm -it dockerdemo-openjdk```
## To view logs by containername
```docker logs myjavaapp-container  ```

## README Document creation Examples
> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

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
docker run --name mysql57 -p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=1234 \
-e MYSQL_USER=demo_java \
-e MYSQL_PASSWORD=1234 \
-e MYSQL_DATABASE=hello_java \
-d mysql/mysql-server:5.7
```

- Table Example

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
