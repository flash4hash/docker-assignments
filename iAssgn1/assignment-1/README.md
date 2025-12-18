# Assignment 1 – Docker Static Website

## Description
This assignment is about creating and running a Docker container that serves a static website using Nginx.

## Files
- index.html
- Dockerfile

## Steps

### Build the Docker image
```bash
docker build -t my-site .
```

### Run the container
```
docker run -d --name web -p 7070:80 my-site
```

### Test
#### Browser:
```bash
http://localhost:7070
```

#### CLI:
```bash
curl http://localhost:7070
```

### Stop and remove the container
```
docker stop web
docker rm web
```

### Notes
* Nginx serves the site on port 80 inside the container.
* Port 7070 on the host is mapped to the container port.

---
