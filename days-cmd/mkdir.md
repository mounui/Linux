mkdir
====

> mkdir 命令用来创建指定的名称的目录，要求创建目录的用户在当前目录中具有写权限，并且指定的目录名不能是当前目录中已有的目录。

### 命令格式

```shell
mkdir [选项] 目录...
```

### 基本功能

通过 mkdir 命令可以实现在指定位置创建以 DirName(指定的文件名)命名的文件夹或目录。要创建文件夹或目录的用户必须对所创建的文件夹的父文件夹具有写权限。并且，所创建的文件夹(目录)不能与其父目录(即父文件夹)中的文件名重名，即同一个目录下不能有同名的(区分大小写)。

### 常用选项

```shell
-Z	# 设置安全上下文，当使用SELinux时有效
-m<目标属性>或--mode<目标属性>	# 建立目录的同时设置目录的权限
-p或--parents	# 若所要建立目录的上层目录目前尚未建立，则会一并建立上层目录
--version 	# 显示版本信息
```

### 常用范例

#### 1.创建一个空目录

```shell
[mao@localhost test]$ mkdir test1
[mao@localhost test]$ ll
总用量 0
drwxrwxr-x. 2 mao mao 6 10月 29 22:15 test1
```

#### 2.递归创建多个目录

```shell
[mao@localhost test]$ mkdir -p test2/test22
[mao@localhost test]$ ll
总用量 0
drwxrwxr-x. 2 mao mao  6 10月 29 22:15 test1
drwxrwxr-x. 3 mao mao 20 10月 29 22:17 test2
[mao@localhost test]$ cd test2
[mao@localhost test2]$ ll
总用量 0
drwxrwxr-x. 2 mao mao 6 10月 29 22:17 test22
```

#### 3.创建权限为777的目录

```shell
[mao@localhost test]$ mkdir -m 777 test3
[mao@localhost test]$ ll
总用量 0
drwxrwxr-x. 2 mao mao  6 10月 29 22:15 test1
drwxrwxr-x. 3 mao mao 20 10月 29 22:17 test2
drwxrwxrwx. 2 mao mao  6 10月 29 22:18 test3
```

#### 4.创建新目录并显示信息

```shell
[mao@localhost test]$ mkdir -v test4
mkdir: 已创建目录 "test4"
[mao@localhost test]$ mkdir -vp test5/test5-1
mkdir: 已创建目录 "test5"
mkdir: 已创建目录 "test5/test5-1"
```

#### 5.一个命令创建项目的目录结构

```shell
[mao@localhost test]$ mkdir -vp scf/{lib/,bin/,doc/{info,product},logs/{info,product},service/deploy/{info,product}}
mkdir: 已创建目录 "scf"
mkdir: 已创建目录 "scf/lib/"
mkdir: 已创建目录 "scf/bin/"
mkdir: 已创建目录 "scf/doc"
mkdir: 已创建目录 "scf/doc/info"
mkdir: 已创建目录 "scf/doc/product"
mkdir: 已创建目录 "scf/logs"
mkdir: 已创建目录 "scf/logs/info"
mkdir: 已创建目录 "scf/logs/product"
mkdir: 已创建目录 "scf/service"
mkdir: 已创建目录 "scf/service/deploy"
mkdir: 已创建目录 "scf/service/deploy/info"
mkdir: 已创建目录 "scf/service/deploy/product"
[mao@localhost test]$ tree scf/
scf/
├── bin
├── doc
│   ├── info
│   └── product
├── lib
├── logs
│   ├── info
│   └── product
└── service
    └── deploy
        ├── info
        └── product

12 directories, 0 files
```
