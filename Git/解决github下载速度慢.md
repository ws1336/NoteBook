# 解决github下载速度慢

### 1. 查找github公网ip,访问如下网址:

> https://fastly.net.ipaddress.com/github.global.ssl.fastly.net
>
> https://github.com.ipaddress.com/

### 2. 修改hosts文件

```shell
sudo nano /etc/hosts
```

将查询到的网址插入

```
127.0.0.1       localhost
127.0.1.1       ws-PC

151.101.185.194 https://github.global.ssl.fastly.net
140.82.113.4    https://github.com
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

### 3.重启网络刷新DNS缓存

```shell
sudo /etc/init.d/networking restart
```





