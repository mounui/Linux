rmdir
===

> mkdir 命令用来创建指定的名称的目录，要求创建目录的用户在当前目录中具有写权限，并且指定的目录名不能是当前目录中已有的目录。

### 命令格式

```shell
rmdir [选项] 目录...
```

### 基本功能

该命令从一个目录中删除一个或多个子目录项，删除某目录时也必须具有对父目录的写权限。

### 常用选项

```shell
-p或--parents	# 删除指定目录后，若该目录的上层目录已变成空目录，则将其一并删除；
--ignore-fail-on-non-empty	# 此选项使rmdir命令忽略由于删除非空目录时导致的错误信息；
-v或-verboes	# 显示命令的详细执行过程；
--help		# 显示命令的帮助信息；
--version	# 显示命令的版本信息。
```

### 常用范例

#### 1.rmdir不能删除非空目录

```shell
[mao@localhost scf]$ tree
.
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
[mao@localhost scf]$ rmdir doc
rmdir: 删除 "doc" 失败: 目录非空
[mao@localhost scf]$ rmdir doc/info
[mao@localhost scf]$ rmdir doc/product
[mao@localhost scf]$ tree
.
├── bin
├── doc
├── lib
├── logs
│   ├── info
│   └── product
└── service
    └── deploy
        ├── info
        └── product

10 directories, 0 files
```

#### 2.`rmdir -p`当子目录被删除后使它也成为空目录的话，则顺便一并删除

```shell
[mao@localhost scf]$ tree
.
├── bin
├── doc
├── lib
├── logs
│   ├── info
│   └── product
└── service
    └── deploy
        ├── info
        └── product

10 directories, 0 files
[mao@localhost scf]$ rmdir -p logs/info
rmdir: 删除目录 "logs" 失败: 目录非空
[mao@localhost scf]$ tree
.
├── bin
├── doc
├── lib
├── logs
│   └── product
└── service
    └── deploy
        ├── info
        └── product

9 directories, 0 files
[mao@localhost scf]$ rmdir -p logs
rmdir: 删除 "logs" 失败: 目录非空
[mao@localhost scf]$ rmdir -p logs/product
[mao@localhost scf]$ tree
.
├── bin
├── doc
├── lib
└── service
    └── deploy
        ├── info
        └── product

7 directories, 0 files
```