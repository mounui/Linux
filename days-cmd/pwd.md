pwd
===

> `pwd`命令来查看”当前工作目录“的完整路径。 简单得说，每当你在终端进行操作时，你都会有一个当前工作目录。 在不太确定当前位置时，就会使用pwd来判定当前目录在文件系统内的确切位置。

### 命令格式

```shell
pwd [选项]
```

### 基本功能

查看”当前工作目录“的完整路径

### 常用选项

```shell
-L （默认值）	# 打印环境变量"$PWD"的值，可能为符号链接。
-P 			# 打印当前工作目录的物理位置。
```

### 常用范例

#### 1.用pwd命令查看默认工作目录的完整路径
```shell
[root@localhost ~]# pwd
/root
```

#### 2.用pwd命令查看指定文件夹
```shell
[root@localhost ~]# cd /opt/soft/
[root@localhost soft]# pwd
/opt/soft
```

#### 3.pwd -P显示出实际路径
```shell
[root@localhost soft]# cd /etc/init.d
[root@localhost init.d]# pwd
/etc/init.d
[root@localhost init.d]# pwd -P
/etc/rc.d/init.d
```

#### 4.当前目录被删除了，而pwd命令仍然显示那个目录
```shell
[root@localhost init.d]# cd /opt/soft
[root@localhost soft]# mkdir removed
[root@localhost soft]# cd removed/
[root@localhost removed]# pwd
/opt/soft/removed
[root@localhost removed]# rm ../removed -rf
[root@localhost removed]# pwd
/opt/soft/removed
```