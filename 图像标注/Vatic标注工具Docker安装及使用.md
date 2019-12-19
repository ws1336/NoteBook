# Vatic标注工具Docker安装及使用

## 一 Vatic的安装

1. 安装Docker,此处不介绍

2. 创建容器

   ```shell
   sudo docker run -it -p 8111:80 -v $MY_VATIC_WORKING_DIR:/root/vatic/data npsvisionlab/vatic-docker /bin/bas
   ```

3. 重新进入容器：使用如下常见的docker指令：

   查询之前容器的container id：

   ```
   sudo docker ps –a
   ```

   开始容器：

   ```
   sudo docker start {container id}
   ```

   进入容器：

   ```
   sudo docker attach {container id}
   ```

## 二 Docker 文件传输

1. Docker 与本地文件传递

   ```shell
   sudo docker cp 本地文件路径 ID全称:容器路径  #本地传递到容器
   sudo docker cp ID全称:容器文件路径 本地路径  #容器传输到本体
   ```

2. 文件压缩方式

   ```shell
#压缩方式：
   tar -zcvf archive_name.tar.gz filename
   #解压缩方式：
   tar -zxvf archive_name.tar.gz 
   ```


## 三 Vatic 使用方法
 1. 启动vatic：

    ```shell
    cd root/vatic
    ./startup.sh	#启动vatic
    turkic list 		#查看当前已存在的数据库
    turkic delete identifier1 --force	#强力删除已存在的某个数据库
    ```
2. 从视频抽取目标图片集合, 内部使用了ffmpeg

   ```shell
   turkic extract ../video/123.mp4 ../output/directory
   #默认是720x480的目标分辨率，也可以添加--no-resize来保证原图的图片质量
   ```

3. 将图片load到数据库

   ```shell
   turkic load identifier1 ../output/directory Label1 Label2 LabelN --blow-radius 0 --skip 5 --offline
   #设置标注的label，每5帧标注1帧，不覆盖周围的帧数据
   #identifier 为标识符,自己起名字 
   ```

4. 发布任务

   ```shell
   turkic publish --offline
   ```

5. 导出pascal数据集

   ```shell
   turkic dump identifier -o ../output/pascal/ --pascal --pascal-skip 1
   ```

6. dump 标注后的元数据

   ```shell
   turkic dump identifier -o output.txt
   #支持xml，json等多种格式
   ```

7. dump标注后的图片数据

   ```shell
   turkic visualize identifier $output_path  --merge  --renumber
   cd $output_path
   #ffmpeg -i %d.jpg -vcodec mpeg4 output.avi
   ffmpeg -r 10 -f image2 -i ./%d.jpg -vcodec libx264 test.mp4
   #支持导出带标注box的图片集合，并可以通过ffmpeg合成为一段完成的演示视频
   ```

参考文献:

> 安装说明:https://www.cnblogs.com/CSGO-416482145/p/many-developer-benefits.html
>
> 使用说明:https://www.jianshu.com/p/46175e5a54ba


