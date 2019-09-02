# Qt 中文输入

首先确保已经安装好搜狗输入法，进入qt安装目录打开终端，将fcitx插件复制到qt安装目录下这两个文件夹中:

```shell
cd Tools/QtCreator/lib/Qt/plugins/platforminputcontexts/
sudo cp /usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libfcitxplatforminputcontextplugin.so ./
cd ../../lib/
sudo cp /usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libfcitxplatforminputcontextplugin.so ./
```

