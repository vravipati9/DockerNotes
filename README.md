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

- Table Example

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
