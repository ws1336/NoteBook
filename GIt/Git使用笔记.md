# Git使用笔记

## 安装

```shell
sudo apt install git
```

## 本地使用

#### 1. 新建仓库

```shell 
git init   #新建仓库
git status #查看仓库状态
```

#### 2. 添加追踪文件

```shell
git add . #追踪当前文件夹所有文件
git add README.md #追踪README.md文件
```

#### 3. 提交更改

```shell
git commit -m "添加了readme"  
```

## 远程提交到github仓库

#### 1. 在github上建立仓库，并复制仓库地址

#### 2. 设置本地仓库与远程仓库地址链接，如：

```shell
git remote add origin https://github.com/ws1336/QT-Thermal-Imager.git
```

#### 3. 提交更改到远程仓库

```shell
git config credential.helper store    #设置保存账号密码
git push --set-upstream origin master #提交，之后输入github账号密码
```

#### 4. 下载仓库最新版本

```shell
git pull
```



