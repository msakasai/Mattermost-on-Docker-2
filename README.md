# Mattermost v5.36 with Focalboard plugin

## Note

Use web server (Nginx) .  
Nginx configure for focalboard plugins in mm v5.36.0.  
Commentouted the SSL settings because localhost.  

`nginx/default.conf`

See  
- https://docs.mattermost.com/administration/changelog.html#focalboard-beta
- https://github.com/mattermost/focalboard/discussions/566
- https://docs.mattermost.com/install/install-ubuntu-1804.html#configuring-nginx-as-a-proxy-for-mattermost-server


## Usage

1. Clone repository
2. (optional) Change Mattermost Dockerfile build argument

docker-compose.yml

```
        build:
            context: mattermost/
            dockerfile: Dockerfile
            args:
                - MM_VER=5.36.0
                - DB_HOST=mm-db
                - DB_PORT=3306
                - DB_NAME=mattermost
                - DB_USER=mmuser
                - DB_PASSWORD=mmpass
                - MM_SITE_URL=http://localhost

```

3. Run docker

```
% ls
docker-compose.yml	mattermost		nginx
```

```
% docker compose up
```

```
% docker compose ps
NAME                SERVICE             STATUS              PORTS
mattermost          mattermost          running             0.0.0.0:8065->8065/tcp, :::8065->8065/tcp, 0.0.0.0:8067->8067/tcp, :::8067->8067/tcp, 0.0.0.0:8074->8074/tcp, :::8074->8074/tcp, 0.0.0.0:8075->8075/tcp, :::8075->8075/tcp
mm-mysql            mm-db               running             0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp
test_mm-web_1       mm-web              running             0.0.0.0:80->80/tcp, :::80->80/tcp
```

4. Access `http://localhost`
5. Sign-up & Create Team
6. Install Focalboard plugin
7. Open Focalboard workspace

![open-focalboard](https://user-images.githubusercontent.com/46712420/122416276-90369280-cfc3-11eb-8f51-fb960ae99ab8.gif)

