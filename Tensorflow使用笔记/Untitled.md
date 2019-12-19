# shell编程

## 一 变量

### 1 变量的定义与使用

```shell
#!/bin/bash
#第一行不可省略
num1=1
num2=2
str1=qwfp
#变量赋值等号两侧不能有空格
echo $num1
echo $num2
echo "变量连接$str1"arst
echo "变量默认都是字符串$num1+$num2"
```

### 2 位置变量与系统预定义变量

[./3.png]!

```shell
#!/bin/bash

echo $@
echo $*
echo $!
echo $%

for s in $@
	do
		echo $s
	done
```



