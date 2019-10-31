rm
===

> rm是常用的命令，该命令的功能为删除一个目录中的一个或多个文件或目录，它也可以将某个目录及其下的所有文件及子目录均删除。对于链接文件，只是删除了链接，原有文件均保持不变。rm是一个危险的命令，使用的时候要特别当心，尤其对于新手，否则整个系统就会毁在这个命令（比如在/（根目录）下执行rm * -rf）。所以，我们在执行rm之前最好先确认一下在哪个目录，到底要删除什么东西，操作时保持高度清醒的头脑。

### 命令格式

```shell
rm [选项] 文件…
```

### 基本功能

删除一个目录中的一个或多个文件或目录，如果没有使用- r选项，则rm不会删除目录。如果使用 rm 来删除文件，通常仍可以将该文件恢复原状。

### 常用选项

```shell
-d	# 直接把欲删除的目录的硬连接数据删除成0，删除该目录
-f	# 强制删除文件或目录
-i	# 删除已有文件或目录之前先询问用户
-r或-R	# 递归处理，将指定目录下的所有文件与子目录一并处理
--preserve-root	# 不对根目录进行递归操作
-v	# 显示指令的详细执行过程
```

### 常用范例

#### 1.删除文件file，系统会先询问是否删除

```shell
[mao@localhost test]$ touch log.log
[mao@localhost test]$ rm -i log.log 
rm：是否删除普通空文件 "log.log"？y	# 输入rm log.log命令后，系统会询问是否删除，输入y后就会删除文件，不想删除则数据n
[mao@localhost test]$ ll
总用量 0
[mao@localhost test]$
```

#### 2.强行删除file，系统不再提示

```shell
[mao@localhost test]$ ll
总用量 0
-rw-rw-r--. 1 mao mao 0 10月 30 22:24 log1.log
[mao@localhost test]$ rm -f log1.log 
[mao@localhost test]$ ll
总用量 0
```

#### 3.删除任何.log文件；删除前逐一询问确认

```shell
[mao@localhost test]$ ll
总用量 0
-rw-rw-r--. 1 mao mao 0 10月 30 22:25 log1.log
-rw-rw-r--. 1 mao mao 0 10月 30 22:25 log2.log
[mao@localhost test]$ rm -i *.log
rm：是否删除普通空文件 "log1.log"？y
rm：是否删除普通空文件 "log2.log"？y
[mao@localhost test]$ ll
总用量 0
```

#### 4.将test1子目录及子目录中所有档案删除

```shell
[mao@localhost test]$ ll
总用量 0
drwxrwxr-x. 2 mao mao  6 10月 30 22:27 scf
drwxrwxr-x. 2 mao mao 22 10月 31 21:51 test1
drwxrwxr-x. 2 mao mao  6 10月 30 22:28 test2
drwxrwxr-x. 2 mao mao  6 10月 30 22:28 test3
drwxrwxr-x. 2 mao mao  6 10月 30 22:28 test4
drwxrwxr-x. 2 mao mao  6 10月 30 22:28 test5
[mao@localhost test]$ rm -r test1
[mao@localhost test]$ ll
总用量 0
drwxrwxr-x. 2 mao mao 6 10月 30 22:27 scf
drwxrwxr-x. 2 mao mao 6 10月 30 22:28 test2
drwxrwxr-x. 2 mao mao 6 10月 30 22:28 test3
drwxrwxr-x. 2 mao mao 6 10月 30 22:28 test4
drwxrwxr-x. 2 mao mao 6 10月 30 22:28 test5
```

#### 5.强制删除目录及其里面的内容

```shell
[mao@localhost test]$ rm -rf test2
[mao@localhost test]$ ll
总用量 0
drwxrwxr-x. 2 mao mao 6 10月 30 22:27 scf
drwxrwxr-x. 2 mao mao 6 10月 30 22:28 test3
drwxrwxr-x. 2 mao mao 6 10月 30 22:28 test4
drwxrwxr-x. 2 mao mao 6 10月 30 22:28 test5
```

#### 6.删除已-f开头的文件

```shell
[mao@localhost test]$ touch -- -f
[mao@localhost test]$ ls -- -f
-f
[mao@localhost test]$ rm -- -f
[mao@localhost test]$ ls -- -f
ls: 无法访问-f: 没有那个文件或目录
```

#### 7.自定义回收站功能

```shell
# 模拟回收站的效果，即删除文件的时候只是把文件放到一个临时目录中，这样在需要的时候还可以恢复过来。
[mao@localhost test]$ myrm(){ D=/tmp/$(date +%Y%m%d%H%M%S); mkdir -p $D; mv "$@" $D && echo "moved to $D ok";}
[mao@localhost test]$ alias rm='myrm'
[mao@localhost test]$ touch {1..3}.log
[mao@localhost test]$ ls
1.log  2.log  3.log  scf  test3  test4  test5
[mao@localhost test]$ rm {1..3}.log
moved to /tmp/20191031220452 ok
[mao@localhost test]$ ls
scf  test3  test4  test5
[mao@localhost test]$ ls /tmp/20191031220452/
1.log  2.log  3.log
```
