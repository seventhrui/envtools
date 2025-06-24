---
icon: plane-departure
---

# gost

{% stepper %}
{% step %}
安装服务

```
wget https://github.com/go-gost/gost/releases/download/v3.0.0/gost_3.0.0_linux_amd64v3.tar.gz
tar -zxvf gost_3.0.0_linux_amd64v3.tar.gz
mv gost /usr/bin/gost
chmod +x /usr/bin/gost
```
{% endstep %}

{% step %}
### 配置文件

```
services:
  - name: service-1
    addr: ":8080"
    handler:
      type: socks5
      # type: socks
      auth:
        username: testuser
        password: testpassword
    listener:
      type: tcp    

  - name: service-2
    addr: ":3208"
    handler:
      type: http
      auth:
        username: user
        password: password
    listener:
      type: tcp

```
{% endstep %}

{% step %}
### 安全策略

```
sudo ufw status
sudo ufw allow 8080/tcp
sudo ufw allow 3208/tcp
```
{% endstep %}

{% step %}
### 客户端配置

clash

```
port: 7890
socks-port: 7891
allow-lan: false
mode: global
log-level: info

proxies:
  - name: "GameProxy"
    type: socks5
    server: gost-server-ip
    port: 8080
    username: testuser
    password: testpassword

proxy-groups:
  - name: "GLOBAL"
    type: select
    proxies:
      - GameProxy
```
{% endstep %}
{% endstepper %}
