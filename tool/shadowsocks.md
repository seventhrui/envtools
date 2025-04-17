---
icon: arrow-progress
---

# Shadowsocks

{% stepper %}
{% step %}
### 安装Shadowsocks-libev服务器

1. ```
   sudo apt update
   ```
2. ```
   sudo apt install shadowsocks-libev
   ```
{% endstep %}

{% step %}
### 安装后修改配置文件

```
sudo nano /etc/shadowsocks-libev/config.json
```

该文件的默认内容如下:

```
{
    "server":["::1", "127.0.0.1"],
    "mode":"tcp_and_udp",
    "server_port":8388,
    "local_port":1080,
    "password":"ACRrobo9ymXb",
    "timeout":60,
    "method":"chacha20-ietf-poly1305"
}
```

需要将 `127.0.0.1` 更改为 `0.0.0.0`，以便 Shadowsocks-libev 服务器将监听公共 IP 地址。然后将 `server_port` 更改为其他端口号，例如 8888。密码是随机生成的，因此可以修改或保持原样。

保存并关闭文件。然后重新启动shadowsocks-libev服务以使更改生效。

```
sudo systemctl restart shadowsocks-libev.service
```

启用启动时自动启动。

```
sudo systemctl enable shadowsocks-libev.service
```

检查其状态。确保它正在运行。

```
systemctl status shadowsocks-libev.service
```

如果您看到以下错误。

```
This system doesn't provide enough entropy to quickly generate high-quality random numbers. The service will not start until enough entropy has been collected.
```

您可以通过安装 rng-tools 来修复此错误。

```
sudo apt-get install rng-tools
```

然后运行

```
sudo rngd -r /dev/urandom
```

现在你可以启动Shadowsocks-libev服务了。
{% endstep %}

{% step %}
### 配置防火墙

如果您在服务器上使用 [iptables](https://cn.linux-console.net/?cat=iptables) 防火墙，则需要允许流量流向 Shadowsocks 正在侦听的 TCP 和 UDP 端口。例如，如果 Shadowsocks 使用端口 8888，则运行以下命令：

```
sudo iptables -I INPUT -p tcp --dport 8888 -j ACCEPT

sudo iptables -I INPUT -p udp --dport 8888 -j ACCEPT
```

如果您使用 UFW 防火墙，请运行以下命令：

```
sudo ufw allow 8888
```

如果您使用云服务器，则需要在安全策略中添加端口。
{% endstep %}
{% endstepper %}

