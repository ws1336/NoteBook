# 编译安装OpenCV

### 首先安装依赖包

```shell
sudo apt-get install build-essential　#编译
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev　#依赖
sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev　#可选
```

### 创建编译文件夹用来存放编译生成的文件

```shell
cd ~/opencv
mkdir build
cd build
```

### 编译

```shell
cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local ..
make -j7 # 用７个线程进行编译
sudo make install 
```

### 测试

新建如下new.cpp文件,同级目录存放一张名称为‘test.jpg’的图片

```c++
#include <iostream>
#include <opencv2/opencv.hpp>
using namespace cv;
using namespace std;
int main()
{
        Mat img = imread("test.jpg");
        imshow("test",img);
        waitKey(0);
        return 0;
}
```

使用如下命令进行编译

```shell
g++ new.cpp -o test `pkg-config opencv --libs --cflags`
```

![图片](/home/ws/图片/2019-08-29 15-15-01屏幕截图.png)

### 其它

#### 1. 编译过程中可能遇到缺少如下错误导致编译失败

> fatal error: Eigen/Core: 没有那个文件或目录

这是由于Eigen没有安装导致的，解决方案如下
```shell
sudo apt install libeigen3-dev 
sudo ln -s /usr/include/eigen3/Eigen /usr/include/Eigen
```

```shell
sudo apt install libeigen3-dev 
sudo ln -s /usr/include/eigen3/Eigen /usr/include/Eigen
```

安装后重新编译即可

#### 2. 未定义的引用

> Opencv undefined reference to `cv::imread()

这种错误可能是因为Qt中的lib路径设置错了，请仔细检查，注意行尾反斜杠，正确配置可以如下图（3.4版本成功，4.1不行）

```makefile
INCLUDEPATH+=/usr/local/include/opencv/opencv2\
/usr/local/include/opencv\
/usr/local/include

LIBS+=/usr/local/lib/libopencv_*.so
```

#### 3.运行时链接库报错

> error while loading shared libraries: libopencv_core.so.3.4: cannot open shared object file: No such file or directory

由于系统找不到so文件导致，解决如下

```shell
cd /etc/ld.so.conf.d/
sudo nano OpenCV.conf
```

输入以下内容

`/usr/local/lib`
然后shell

```shell
sudo ldconfig
```



`` ``