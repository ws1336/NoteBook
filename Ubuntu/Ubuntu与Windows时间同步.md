# Ubuntu 与 Windows 时间同步

终端输入如下

```shell
sudo apt-get install ntpdate
sudo ntpdate time.windows.com
sudo hwclock --localtime --systohc
```

