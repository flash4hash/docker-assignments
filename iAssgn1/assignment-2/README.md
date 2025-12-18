# **Assignment 2 – Container Communication Using Docker Network**

## Description
This assignment demonstrates communication between two Docker containers using a custom Docker network.

One container runs a static web server (Nginx) and the other runs a simple API using a prebuilt image.

## Docker Network
Create a custom network:
```bash
docker network create webnet
```

## API Container
Run the API container on the custom network:
```
docker run -d --name api --network webnet hashicorp/http-echo -text="Hello from API"
```
This container listens on port 5678 and responds with a simple text message.

## Web Container
Run the Nginx container on the same network:
```
docker run -d --name web --network webnet -p 7070:80 nginx:alpine
```

## Testing Container Communication
Test API access from inside the web container:
```
docker exec -it web curl http://api:5678
```

Expected output:
```
Hello from API
```
This confirms that the web container can reach the API container using the container name over the Docker network.

---

## Cleanup
Stop and remove containers:
```
docker stop web api
docker rm web api
```
