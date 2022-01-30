# Create Dockerfile

in the root project create file name is **dockerfile**

```docker
FROM [baseimage]
WORKDIR [current working directory]
COPY [source] [target]
RUN [command]
EXPOSE [port]
CMD [command]
ENTRYPOINT ["command"]
```



## VueX | Multi Stage Build (Tutorial Frontend)

- Create new file into project top root path
  
- Copy code following below 
  
```dockerfile
# build stage
FROM node:lts-alpine as build-stage
WORKDIR /app
COPY ./entrypoint.sh /entrypoint.sh
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# production stage
FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /app/dist /usr/share/nginx/html
COPY --from=build-stage /app/entrypoint.sh /usr/share/nginx/html

EXPOSE 80

COPY ./entrypoint.sh /entrypoint.sh

# Grant Linux permissions and run entrypoint script
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
```

### Command Build

```bash
docker build -t tutorial-fe:0.0.1 .
```

### Command Run
```bash
docker run -it --rm --name tutorial-frontend -p 80:80 -e VUE_APP_ENPOINT_API_BACKEND=http://{IPADDR}:8089/api tutorial-fe:0.0.1
```



## Golang | Multi stage build (Tutorial Backend)

- Create new file into project top root path
- Copy code following below 
  
```dockerfile
FROM golang:1.17-alpine
WORKDIR /go/src/github.com/tarathep/tutorial-backend/
RUN go get -d -v github.com/gin-gonic/gin
RUN go get -d -v github.com/stretchr/testify
RUN go get -d -v go.mongodb.org/mongo-driver
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .

FROM alpine:latest  
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=0 /go/src/github.com/tarathep/tutorial-backend/app ./
CMD ["./app"]
```

### Command Build

```bash
docker build -t tutorial-be:0.0.1 .
```

### Command Run
```bash
docker run -it --rm --name tutorial-backend -p 8089:8089 -e MONGODB_CONNECTION_STRING=mongodb://root:password@192.168.1.102:27017 tutorial-be:0.0.1
```