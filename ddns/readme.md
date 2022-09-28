#### DDNS 客户端

##### 项目地址：https://github.com/jeessy2/ddns-go

当前目录 `docker compose up -d` 即可运行

旧版 compose 命令中间有横线 `docker-compose up -d`

运行后浏览器访问 `http://YOUR_IP:9876` 进行配置

由于网络模式为host, Linux 端口不能访问请检查防火墙, 
Windows 或 Mac 请使用 bridge 模式并添加端口映射, 如下:

```yml
version: '3'
services:
  ddns-go:
    container_name: ddns
    restart: always
    network_mode: bridge
    volumes:
      - ./data:/root
    image: jeessy/ddns-go
    ports:
      - 9876:9876
```