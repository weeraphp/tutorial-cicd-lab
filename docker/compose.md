# Docker Compose

1. Create directory (folder) name is tutorial-stack
    ```bash
    mkdir tutorial-stack
    ```


2. Copy Tutoral Projects into tutorial-stack

    
3. Create docker-compose.yaml file in tutorial-stack on root path.

4. Copy & Paste Code into **docker-compose.yaml**


    ```docker-compose
    version: "3"

    services:
    frontend:
        build: ./[name]-tutorial-frontend
        volumes:
        - ./tutorial-frontend:/app
        ports:
        - "80:80"
        environment:
        VUE_APP_ENPOINT_API_BACKEND: "http://127.0.0.1:8089/api"
        networks:
        - front-tier
    
    backend:
        build: ./[name]-tutorial-backend
        depends_on:
        - "db"
        volumes:
        - ./tutorial-backend:/app
        ports:
        - "8089:8089"
        environment:
        MONGODB_CONNECTION_STRING: "mongodb://root:password@mongodb:27017"
        networks:
        - back-tier
        - front-tier

    mongodb:
        image: mongo:latest
        container_name: mongodb
        environment:
        MONGO_INITDB_ROOT_USERNAME: "root"
        MONGO_INITDB_ROOT_PASSWORD: "password"
        volumes:
        - "db-data:/data/db"
        networks:
        - back-tier

    volumes:
    db-data:

    networks:
    front-tier:
    back-tier:
    ```
5. run command stack

```
docker compose up -d
```

