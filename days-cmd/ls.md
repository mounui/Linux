ls
===

> ls命令是linux下最常用的命令。ls命令就是list的缩写，缺省下ls用来打印出当前目录的清单，如果ls指定其他目录，那么就会显示指定目录里的文件及文件夹清单。 通过ls 命令不仅可以查看linux文件夹包含的文件，而且可以查看文件权限(包括目录、文件夹、文件权限)，查看目录信息等等。ls 命令在日常的linux操作中用的很多!

### 命令格式

```shell
ls	[选项] 	[目录名]
```

### 基本功能

列出目标目录中所有的子目录和文件。

### 常用选项

```shell
-C     # 多列输出，纵向排序。
-F     # 每个目录名加 "/" 后缀，每个 FIFO 名加 "|" 后缀， 每个可运行名加“ * ”后缀。
-R     # 递归列出遇到的子目录。
-a     # 列出所有文件，包括以 "." 开头的隐含文件。
-c     # 使用“状态改变时间”代替“文件修改时间”为依据来排序（使用“-t”选项时）或列出（使用“-l”选项时）。
-d     # 将目录名象其它文件一样列出，而不是列出它们的内容。
-i     # 输出文件前先输出文件系列号（即 i 节点号: i-node number）。 -l  列出（以单列格式）文件模式（file mode），文件的链     接数，所有者名，组名，文件大小（以字节为单位），时间信息，及文件名。缺省时，时间信息显示最近修改时间；可以以选项“-c”和“-u”选择显示其它两种时间信息。对于设    备文件，原先显示文件大小的区域通常显示的是主要和次要的号（majorand minor device numbers）。
-q     # 将文件名中的非打印字符输出为问号。（对于到终端的输出这是缺省的。）
-r     # 逆序排列。
-t     # 按时间信息排序。
-u     # 使用最近访问时间代替最近修改时间为依据来排序（使用“-t”选项时）或列出（使用“-l”选项时）。
-1     # 单列输出。
-1, --format=single-column  # 一行输出一个文件（单列输出）。如标准输出不是到终端，此选项就是缺省选项。
-a, --all # 列出目录中所有文件，包括以“.”开头的文件。
-b, --escape # 把文件名中不可输出的字符用反斜杠加字符编号(就象在 C 语言里一样)的形式列出。
-c, --time=ctime, --time=status
      # 按文件状态改变时间（i节点中的ctime）排序并输出目录内
      # 容。如采用长格式输出（选项“-l”），使用文件的状态改
      # 变时间取代文件修改时间。【译注：所谓文件状态改变（i节
      # 点中以ctime标志），既包括文件被修改，又包括文件属性（ 如所有者、组、链接数等等）的变化】
-d, --directory
      # 将目录名象其它文件一样列出，而不是列出它们的内容。
-f    #  不排序目录内容；按它们在磁盘上存储的顺序列出。同时启 动“ -a ”选项，如果在“ -f ”之前存在“ -l
      # ”、“ - -color ”或“ -s ”，则禁止它们。
-g    # 忽略，为兼容UNIX用。
-i, --inode
      # 在每个文件左边打印  i  节点号（也叫文件序列号和索引号:  file  serial  number and index num‐
      # ber）。i节点号在每个特定的文件系统中是唯一的。
-k, --kilobytes
      # 如列出文件大小，则以千字节KB为单位。
-l, --format=long, --format=verbose
      # 除每个文件名外，增加显示文件类型、权限、硬链接数、所       有者名、组名、大小（        byte
      # ）、及时间信息（如未指明是      其它时间即指修改时间）。对于6个月以上的文件或超出未来     1
      # 小时的文件，时间信息中的时分将被年代取代。
      # 每个目录列出前，有一行“总块数”显示目录下全部文件所       占的磁盘空间。块默认是        1024
      # 字节；如果设置了   POSIXLY_CORRECT  的环境变量，除非用“  -k  ”选项，则默认块大小是  512  字
      # 节。每一个硬链接都计入总块数（因此可能重复计数），这无 疑是个缺点。

# 列出的权限类似于以符号表示（文件）模式的规范。但是 ls
      # 在每套权限的第三个字符中结合了多位（ multiple bits ） 的信息，如下： s 如果设置了  setuid
      # 位或 setgid   位，而且也设置了相应的可执行位。 S 如果设置了 setuid 位或 setgid
      # 位，但是没有设置相应的可执行位。 t 如果设置了  sticky  位，而且也设置了相应的可执行位。  T
      # 如果设置了 sticky 位，但是没有设置相应的可执行位。              x
      # 如果仅仅设置了可执行位而非以上四种情况。 - 其它情况（即可执行位未设置）。
-m, --format=commas
      # 水平列出文件，每行尽可能多，相互用逗号和一个空格分隔。
-n, --numeric-uid-gid
      # 列出数字化的 UID 和 GID 而不是用户名和组名。
-o    #  以长格式列出目录内容，但是不显示组信息。等于使用“         --format=long          --no-group
      # ”选项。提供此选项是为了与其它版本的 ls 兼容。
-p    #  在每个文件名后附上一个字符以说明该文件的类型。类似“ -F ”选项但是不 标示可执行文件。
-q, --hide-control-chars
      # 用问号代替文件名中非打印的字符。这是缺省选项。
-r, --reverse
      # 逆序排列目录内容。
-s, --size
      # 在每个文件名左侧输出该文件的大小，以    1024   字节的块为单位。如果设置了   POSIXLY_CORRECT
      # 的环境变量，除非用“ -k ”选项，块大小是 512 字节。
-t, --sort=time
      # 按文件最近修改时间（ i 节点中的 mtime ）而不是按文件名字典序排序，新文件 靠前。
-u, --time=atime, --time=access, --time=use
      # 类似选项“    -t    ”，但是用文件最近访问时间（    i     节点中的     atime     ）取代文件修
      # 改时间。如果使用长格式列出，打印的时间是最近访问时间。
-w, --width cols
       # 假定屏幕宽度是      cols      （      cols     以实际数字取代）列。如未用此选项，缺省值是这
       # 样获得的：如可能先尝试取自终端驱动，否则尝试取自环境变量          COLUMNS          （如果设
       # 置了的话），都不行则取 80 。

-x, --format=across, --format=horizontal
       # 多列输出，横向排序。

-A, --almost-all
       # 显示除 "." 和 ".." 外的所有文件。

-B, --ignore-backups
       # 不输出以“ ~ ”结尾的备份文件，除非已经在命令行中给出。

-C, --format=vertical
       # 多列输出，纵向排序。当标准输出是终端时这是缺省项。使用命令名 dir 和 d 时， 则总是缺省的。

-D, --dired
       # 当采用长格式（“-l”选项）输出时，在主要输出后，额外打印一行：  //DIRED//  BEG1 END1 BEG2
       # END2 ...

# BEGn 和 ENDn 是无符号整数，记录每个文件名的起始、结束位置在输出中的位置（
#        字节偏移量）。这使得          Emacs          易于找到文件名，即使文件名包含空格或换行等非正
#        常字符也无需特异的搜索。
#
# 如果目录是递归列出的（“ -R ”选项），每个子目录后列出类似一行：
       # //SUBDIRED//  BEG1 END1 ...  【译注：我测试了 TurboLinux4.0 和 RedHat6.1 ，发现它们都是在 “
       # //DIRED//     BEG1...     ”之后列出“     //SUBDIRED//     BEG1     ...      ”，也即只有一个
       # 而不是在每个子目录后都有。而且“ //SUBDIRED// BEG1 ... ”列出的是各个子目 录名的偏移。】

-F, --classify, --file-type
       # 在每个文件名后附上一个字符以说明该文件的类型。“  * ”表示普通的可执行文件； “ / ”表示目录；“
       # @ ”表示符号链接；“ | ”表示FIFOs；“ = ”表示套接字 (sockets) ；什么也没有则表示普通文件。

-G, --no-group
       # 以长格式列目录时不显示组信息。

-I, --ignorepattern
       # 除非在命令行中给定，不要列出匹配shell文件名匹配式（pattern ，不是指一般
       # 表达式）的文件。在shell中，文件名以"."起始的不与在文件名匹配式(pattern)
       # 开头的通配符匹配。

-L, --dereference
       # 列出符号链接指向的文件的信息，而不是符号链接本身。

-N, --literal
       # 不要用引号引起文件名。

-Q, --quote-name
       # 用双引号引起文件名，非打印字符以 C 语言的方法表示。

-R, --recursive
       # 递归列出全部目录的内容。

-S, --sort=size
       # 按文件大小而不是字典序排序目录内容，大文件靠前。

-T, --tabsize cols
       # 假定每个制表符宽度是 cols 。缺省为 8。为求效率， ls 可能在输出中使用制表符。  若 cols 为
       0，则不使用制表符。

-U, --sort=none
       # 不排序目录内容；按它们在磁盘上存储的顺序列出。（选项“-U”和“-f”的不
       # 同是前者不启动或禁止相关的选项。）这在列很大的目录时特别有用，因为不加排序
       # 能显著的加快速度。

-X, --sort=extension
       # 按文件扩展名（由最后的 "." 之后的字符组成）的字典序排序。没有扩展名的先列 出。

--color[=when]
       # 指定是否使用颜色区别文件类别。环境变量  LS_COLORS  指定使用的颜色。如何设置 这个变量见 dir‐
       # colors(1) 。 when 可以被省略，或是以下几项之一：
none # 不使用颜色，这是缺省项。
       # auto 仅当标准输出是终端时使用。 always 总是使用颜色。指定 --color 而且省略 when  时就等同于
       # --color=always 。

--full-time
       # 列出完整的时间，而不是使用标准的缩写。格式如同          date(1)          的缺省格式；此格式
       # 是不能改变的，但是你可以用 cut(1) 取出其中的日期字串并将结果送至命令 “ date -d ”。

# 输出的时间包括秒是非常有用的。（ Unix 文件系统储存文件的时间信息精确到秒，
       # 因此这个选项已经给出了系统所知的全部信息。）例如，当你有一个         Makefile          文件
       # 不能恰当的生成文件时，这个选项会提供帮助。
```

### 常用范例

#### 1.列出/home/peidachang文件夹下的所有文件和目录的详细资料

```shell
ls -l -R /home/peidachang
```

在使用 ls 命令时要注意命令的格式：在命令提示符后，首先是命令的关键字，接下来是命令参数，在命令参数之前要有一短横线“-”，所有的命令参数都有特定的作用，自己可以根据需要选用一个或者多个参数，在命令参数的后面是命令的操作对象。在以上这条命令“ ls -l -R /home/peidachang”中，“ls” 是命令关键字，“-l -R”是参数，“ /home/peidachang”是命令的操作对象。在这条命令中，使用到了两个参数，分别为“l”和“R”，当然，你也可以把他们放在一起使用，如下所示：

```shell
ls -lR /home/peidachang
```

这种形式和上面的命令形式执行的结果是完全一样的。另外，如果命令的操作对象位于当前目录中，可以直接对操作对象进行操作;如果不在当前目录则需要给出操作对象的完整路径，例如上面的例子中，我的当前文件夹是peidachang文件夹，我想对home文件夹下的peidachang文件进行操作，我可以直接输入 ls -lR peidachang，也可以用 ls -lR /home/peidachang。

#### 2.列出当前目录中所有以“t”开头的目录的详细内容

```shell
ls -l t*
```

可以查看当前目录下文件名以“t”开头的所有文件的信息。其实，在命令格式中，方括号内的内容都是可以省略的，对于命令ls而言，如果省略命令参数和操作对象，直接输入“ ls ”，则将会列出当前工作目录的内容清单。

#### 3.只列出文件下的子目录

```shell
[root@localhost opt]# ls -F /opt/soft | grep /$ 	# 列出 /opt/soft 文件下面的子目录
jdk1.6.0_16/
subversion-1.6.1/
tomcat6.0.32/

[root@localhost opt]#  ls -l /opt/soft | grep "^d"		# 列出 /opt/soft 文件下面的子目录详细情况
drwxr-xr-x 10 root root      4096 09-17 18:17 jdk1.6.0_16
drwxr-xr-x 16 1016 1016      4096 10-11 03:25 subversion-1.6.1
drwxr-xr-x  9 root root      4096 2011-11-01 tomcat6.0.32
```

#### 4.列出目前工作目录下所有名称是s 开头的档案，愈新的排愈后面

```shell
[root@localhost opt]# ls -ltr s* 	# 列出目前工作目录下所有名称是s 开头的档案，愈新的排愈后面
src:
总计 0
script:
总计 0
soft:
总计 350644
drwxr-xr-x  9 root root      4096 2011-11-01 tomcat6.0.32
-rwxr-xr-x  1 root root  81871260 09-17 18:15 jdk-6u16-linux-x64.bin
drwxr-xr-x 10 root root      4096 09-17 18:17 jdk1.6.0_16
-rw-r--r--  1 root root 205831281 09-17 18:33 apache-tomcat-6.0.32.tar.gz
-rw-r--r--  1 root root   5457684 09-21 00:23 tomcat6.0.32.tar.gz
-rw-r--r--  1 root root   4726179 10-10 11:08 subversion-deps-1.6.1.tar.gz
-rw-r--r--  1 root root   7501026 10-10 11:08 subversion-1.6.1.tar.gz
drwxr-xr-x 16 1016 1016      4096 10-11 03:25 subversion-1.6.1
```

#### 5.列出目前工作目录下所有档案及目录;目录于名称后加"/", 可执行档于名称后加"\*"

```shell
[root@localhost opt]# ls -AF
log/  script/  soft/  src/  svndata/  web/
```

#### 6.计算当前目录下的文件数和目录数

```shell
ls -l * |grep "^-"|wc -l 	# ---文件个数
ls -l * |grep "^d"|wc -l    # ---目录个数
```

#### 7.在ls中列出文件的绝对路径

```shell
[root@localhost opt]# ls | sed "s:^:`pwd`/:"
/opt/log
/opt/script
/opt/soft
/opt/src
/opt/svndata
/opt/web
```

#### 8.列出当前目录下的所有文件（包括隐藏文件）的绝对路径， 对目录不做递归

```shell
[root@localhost opt]# find $PWD -maxdepth 1 | xargs ls -ld
drwxr-xr-x 8 root root 4096 10-11 03:43 /opt
drwxr-xr-x 2 root root 4096 2012-03-08 /opt/log
drwxr-xr-x 2 root root 4096 2012-03-08 /opt/script
drwxr-xr-x 5 root root 4096 10-11 03:21 /opt/soft
drwxr-xr-x 2 root root 4096 2012-03-08 /opt/src
drwxr-xr-x 4 root root 4096 10-11 05:22 /opt/svndata
drwxr-xr-x 4 root root 4096 10-09 00:45 /opt/web
```

#### 9.递归列出当前目录下的所有文件（包括隐藏文件）的绝对路径

```shell
find $PWD | xargs ls -ld
```

#### 10.指定文件时间输出格式

```shell
[root@localhost soft]# ls -tl --time-style=full-iso
总计 350644
drwxr-xr-x 16 1016 1016 4096 2012-10-11 03:25:58.000000000 +0800 subversion-1.6.1

[root@localhost soft]# ls -ctl --time-style=long-iso
总计 350644
drwxr-xr-x 16 1016 1016      4096 2012-10-11 03:25 subversion-1.6.1
```

### 扩展
1. 显示彩色目录列表
	打开/etc/bashrc, 加入如下一行:
	alias ls="ls --color"
	下次启动bash时就可以像在Slackware里那样显示彩色的目录列表了, 其中颜色的含义如下:
2. 蓝色-->目录
3. 绿色-->可执行文件
4. 红色-->压缩文件
5. 浅蓝色-->链接文件
6. 灰色-->其他文件