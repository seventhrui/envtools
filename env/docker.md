---
icon: docker
---

# Docker

1. install docker

```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
docker --version
```

2. install docker compose

```
 sudo curl -L https://github.com/docker/compose/releases/download/v2.40.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
 sudo chmod +x /usr/local/bin/docker-compose
 docker-compose -v
```

3. change source

```
vim /etc/docker/daemon.json
```

```
{
    "registry-mirrors": [
        "https://mirror.ccs.tencentyun.com",
        "https://hub-mirror.c.163.com",
        "https://docker.mirrors.ustc.edu.cn",
        "https://dockerpull.org",
        "https://docker.unsee.tech/",
        "https://docker.1panel.live/",
        "https://docker.udayun.com/",
        "https://docker.nastool.de/"
    ],
    "insecure-registries": [
        "registry.docker-cn.com",
        "docker.mirrors.ustc.edu.cn"
    ],
    "debug": true,
    "experimental": true
}
```

```
systemctl daemon-reload
systemctl restart docker
```
