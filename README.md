# Fully Local and Dockerized QuakeJS Server

This project enables you to run a fully independent, self-contained QuakeJS server using Docker. The server is entirely local, with no reliance on external providers such as `content.quakejs.com` or `quakejs.com`. Once set up, it requires no internet connection, making it ideal for offline gaming sessions.

## Features
- **Completely Independent**: All necessary content is bundled, removing the need for external downloads.
- **Dockerized**: Simple to set up and run using Docker.
- **Offline Capable**: Enjoy fragging with friends and coworkers without any internet dependency.

---

## Quick Start

### 1. Pull the Image  
```bash
docker pull treyyoder/quakejs:latest
```

### 2. Run the Container  
Replace `<HTTP_PORT>` with your desired port (e.g., 8080).  

```bash
docker run -d --name quakejs -e HTTP_PORT=<HTTP_PORT> -p <HTTP_PORT>:80 -p 27960:27960 treyyoder/quakejs:latest
```

#### Example:
```bash
docker run -d --name quakejs -e HTTP_PORT=8080 -p 8080:80 -p 27960:27960 treyyoder/quakejs:latest
```

### 3. Share the Link  
Send the server URL (e.g., `http://localhost:8080`) to your friends or coworkers and start playing! 🎮

---

## Advanced Configuration

### `server.cfg`  
To customize your server, refer to the [Quake3World documentation](https://www.quake3world.com) for guidance on configuring the `server.cfg` file.

---

## Using Docker Compose

You can also use Docker Compose for simplified management:

### `docker-compose.yml`
```yaml
version: '2'
services:
    quakejs:
        container_name: quakejs
        environment:
            - HTTP_PORT=8080
        ports:
            - '8080:80'
            - '27960:27960'
        image: 'treyyoder/quakejs:latest'
```

Run the server with:
```bash
docker-compose up -d
```

---

## Building the Image Locally

If you'd like to build the image from the source:

1. Clone this repository:
   ```bash
   git clone https://github.com/your-repo/quakejs-docker.git
   cd quakejs-docker
   ```

2. Update line endings for `Dockerfile` and `entrypoint.sh`:
   Convert files from **CRLF** to **LF**.

3. Build the image:
   ```bash
   docker build --add-host=content.quakejs.com:127.0.0.1 -t treyyoder/quakejs:latest .
   ```

## Credits- Trey Yoder
https://github.com/treyyoder
