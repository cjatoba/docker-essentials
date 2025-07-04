## Dockerfile

- Take advantage of the layers, each dockerfile command is created in a cache, when a line is changed the lines below are rebuilt, so keep the commands that have the most possibility of changes on the last lines and the commands with the least probability of changes on the top lines;
- Only use one RUN command as each RUN creates a layer on the image making the image very large;
- Use the .dockerignore file to tell docker which files should be ignored in the COPY command, for example;
- When using the COPY or WORKDIR command, docker already creates the directories if they don't exist, so no additional command is needed to create the folders;
- Use Multi Stage Build when two dockerfiles are needed, for example a project that needs a dockerfile to build an application and another dockerfile to use only the executable, the first FROM can be named (in the example for build) and then we can use one more FROM command of a smaller image and in the COPY command copy only the executable of the previous FROM, in this way the image is smaller, just with the size of the second FROM:

```docker
FROM golang:1.8.3 as build
WORKDIR /go/src/github.com/alexellis/href-counter/
RUN go get -d -v golang.org/x/net/html  
COPY app.go .
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .

FROM alpine:latest  
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=build /go/src/github.com/alexellis/href-counter/app .
CMD ["./app"]
```

## Container

- Keep each container with only one responsibility, in a php application with Nginx for example, create a container for Nginx and a container with PHP for the application;
