# 一.创建新的虚拟机步骤
- 记得添加CD/DVD的文件路径(即CentOS-7-x86 64-DVD的路径)或者在创建的时候直接添加也可以
- 新建时,记得网络连接选择桥接网络.
- 开启新建虚拟机,进行设置.
	- 1.语言选择中文简体
	- 2.在安装信息摘要里,点击安装位置进去,然后不做任何修改,直接完成
	- 3.点击软件选择,只执行命令测试可以选择最小安装,右侧全选;若是想选择友好的图形交互界面,可以选择GNOME桌面,右侧全选,点击完成.
	- 4.选择网络和主机名选项,进入,打开以太网开关,点击完成
	- 5.然后点击右下角的安装,在安装进行界面,点击ROOT密码,进行root密码设置,设置完成后,等待安装成功
	
# 二.Linux命令
- Linux命令的通用命令格式
	- 命令字  [选项]  [参数]
		- 选项: 用于调节命令的具体功能
		- 参数: 命令操作的对象，如文件、目录名等

- 目录操作命令
	- pwd,cd,ls,mkdir,du
- 文件操作命令
	- touch,file,cp,rm,mv,which,find

- 文件内容操作命令
	- cat,more,less,head,tail,wc,grep

- 压缩命令
	- gzip,bzip2,tar

- ls: 显示文件和目录列表(list)
	- 常用参数：
		- -l (long)	详细信息显示
 		- -a(all)         显示所有子目录和文件的信息，包括隐藏文件  
		- -t	(time)
		- -A	类似于"-a",但不显示"."和".."目录的信息
		- -R	递归显示内容

- du命令: 统计目录及文件的空间占用情况（estimate file space  usage）
	- -a: 统计时包括所有的文件,而不仅仅只统计目录
	- -h: 以更易读的字节单位（K、M等）显示信息
	- -s: 统计每个参数所占用空间总的大小
	
- file: 查看文件类型
	- file 文件名

- cp命令: 复制（copy）文件或目录
	- -r: 递归复制整个目录树
	- -p: 保持源文件的属性不变
	- -f: 强制覆盖目标同名文件或目录
	- -i: 需要覆盖文件或目录时进行提醒

- rm命令：删除（Remove）文件或目录
	- 格式: rm   [选项]   文件或目录
	- 常用命令选项
		- -f: 强行删除文件，不进行提醒
		- -i: 删除文件时提醒用户确认
		- -r: 递归删除整个目录树

-  mv命令: 移动（Move）文件或目录—— 如果目标位置与源位置相同,则相当于改名
	- 格式: mv   [选项]...   源文件或目录…   目标文件或目录

- which命令: 显示系统命令所在目录
	- which <选项> 命令名称
	- 常用命令选项
	- -a	将所有由PATH路径中可以找到的指令均列出,而不止第一个被找到的指令名称

- 内部命令：属于Shell解析器的一部分
	- cd 切换目录（change directory）
	- pwd 显示当前工作目录（print working directory）
	- help 帮助

- 外部命令: 独立于Shell解析器之外的文件程序
	- ls 显示文件和目录列表（list）
	- mkdir 创建目录（make directoriy）
	- cp 复制文件或目录（copy）
	
- 查看帮助文档
	- 内部命令: help + 命令（help cd）
	- 外部命令: man + 命令（man ls）

- 重启命令(root用户才可用)
	- shutdown -r now (立即重启)
	- shutdown -r 时间 (多长分钟后自动启动)
	- shutdown -r 13:30 在时间为13:30时重启
	- 如果是通过shutdown命令设置重启的话,可以用shutdown -c命令取消重启

- 关机命令
 
	- halt 	立刻关机
	- poweroff 	立刻关机
	- shutdown -h now 	立刻关机(root用户使用)
	- shutdown -h 10 	10分钟后自动关机

- Linux运行级别:
![Linux运行级别](https://upload-images.jianshu.io/upload_images/14467627-90fd4261dab3737d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
	- runlevel  切换前的运行级别,当前的运行级别(第一个数字代表未切换过的运行级别)
	- init N 	N代表临时要切换到的运行级别
- 查看主机名
	- hostname

- 修改主机名
	- hostname 主机名 (一次性修改，重启后变回原来的)
	- vi /etc/hostname	(永久修改,修改的时配置文件)

- 测试网络连接
	- ping 主机名 (按Ctrl+c停止)


- 查看网络接口信息
	- 执行ifconfig命令
	- 如果执行不了,需要安装,执行yum install net-tools 命令进行安装
			- 安装途中,要选择y继续安装,如果不想进行选择,可以直接执行yum install net-tools -y命令,就不会让你进行选择了
- 重启network网络服务

	- service network restart
- 设置防火墙

	- service firewalld status	查看防火墙状态
	- systemctl stop firewalld	临时关闭
	- systemctl disable firewalld	禁止开机启动

- /etc/hosts 文件	保存主机名与IP地址的映射记录


- su 切换到root用户

- exit 退出到登录时的用户
- :q 退出
- :q! 强制退出(修改不保存)
- :wq 保存修改退出
- 进入修改时,按i就会出现inset选项,按esc退出修改

# vi文本编辑器
- vim是vi的增强版
- 插入命令
	- i:在光标前插入
	- I:在光标当前行开始插入
	- a:在光标后插入
	- A:在光标当前行末尾插入
	- o:在光标当前行的下一行插入新行
	- O:在光标当前行的上一行插入新行

- 定位命令
	- :set nu	显示行号
	- :set nonu	取消行号
	- gg		到文本的第一行
	- G			到文本的最后一行
    - nG		移到第n行
	- :n		到文本的第n行
	- h 		左移一个字符
	- l			右移一个字符
	- j			下移一行
	- k			上移一行
	- $			移至行尾
	- 0			移至行首

- 删除命令
	- dd:删除当前行
	- ndd:删除光标所在当前行向下数n行
	- D:删除当前行光标所在的位置后面的字符
	- x:向后删除光标所在位置的字符
	- X:向前删除光标前面的字符
	- nX:删除前面的n个字符,光标所在的字符将不会被删
	
- 复制和粘贴命令
	- yy或Y:复制当前行
	- nyy或nY:复制以下n行
	- p:在光标后面插入buffer中的内容
	- P:在光标前面插入buffer中的内容
	
- 替换和撤销命令
	- r:取代光标所在处的字符
	- R:从光标所在处开始替换字符，按esc结束
	- u:撤销上一步操作
	
- 查找操作
	- :set nu	设置行号
	- :set nonu	取消行号
	- :n	移到第n行
	- :/查找的关键字
	
- 替换操作
	- :s /old/new	将当前行中查找到的第一个字符“old” 串替换为“new”
	- :s /old/new/g	将当前行中查找到的所有字符串“old” 替换为“new”
	- :#,# s/old/new/g 	在行号“#,#”范围内替换所有的字符串“old”为“new”
	- :% s/old/new/g	在整个文件范围内替换所有的字符串“old”为“new”
	- :%s/old/new	查找文件中所有行第一次出现的old，替换为new
	
- 其他命令
	- :W[文件路径]保存当前文件
	- :q 如果未对文件做改动则退出
	- :q! 放弃存储名退出
	- :wq或:x 保存退出

- 可视模式
	- v:可视模式
	- V:可视行模式
	- Ctrl+v:可视块模式
	- 注意:
		- 在所有可视模式中,d和x键可以用删除选定的内容
		- 在可视块模式中,选中所需行,按I键输入内容,之后按两次esc键,可在所有选定行光标处添加同样的内容.
# 用户管理命令
- 添加用户命令:useradd
    - u 指定组ID
	- g 指定所属的组名
	- G 指定多个组,用逗号","分开
	- c 用户描述
	- e 失效时间

- 例子含义:创建用户id为888,所属组为users,且还指定了组sys,root的用户zhangsan,其描述为"hr zhang"用户,设置密码
	- useradd -u 888 -g users -G sys,root -c "hr zhang" zhangsan
	- passwd zhangsan
	
- 设置密码命令格式:passwd   [选项]  <用户名>	
	- d 清空用户的密码,使之无需密码即可登录
	- l 锁定用户账户
	- S 查看用户账号的状态(是否被锁定)
	- u 解锁用户账号
	- x 最大密码使用时间(天)
	- n 最小密码使用时间(天)
	
- 修改已有用户属性
	- 修改用户命令:usermod (user modify)
		- -l 修改用户名(login); 例子:usermod -l a b（b改为a）
		- -g 添加组 ;例子:usermod -g sys tom
		- -G 添加多个组 ;例子:usermod -G sys,root tom
		- –L 锁定用户账号密码(Lock);
		- –U 解锁用户账号(Unlock)
	- 删除用户命令:userdel(user delete)
		- -r 删除账号时同时删除目录(remove)[把用户的宿主目录一并删除]

# 组命令管理
- 添加组:groupadd
	- -g 指定gid
- 修改组:groupmod
	- -n 更改组名(new group)
- 删除组: groupdel
- groups 显示用户所属组
- 修改用户组的属性
	- 命令格式: groupmod [选项]  <用户名>
	- 常用命令选项
		- -g: 设置想要使用的GID
		- -o: 使用已经存在的GID
		- -n: 设置想要使用的群组名称
- 设置组帐号密码(极少用),添加/删除组成员
	- 命令格式:gpasswd  [选项]  组帐号名
	- 常用命令选项
		- -a: 向组内添加一个用户
		- -d: 从组内删除一个用户成员
		- -M: 定义组成员列表,以逗号分隔

- 删除组账号
	- 命令格式：groupdel   <组账号名>
	- 注意：只能删除那些没有被任何用户指定为主组的组.
- 显示用户所属组
	- 命令格式: groups	[用户名]
# 文件目录权限管理
- 权限
	- 读(r): 读取文件的内容;列出目录里的对象
	- 写(w):允许修改文件；在目录里面新建或者删除文件
	- 执行(x):允许执行文件;允许进入目录里
- 数字权限

	- 除了用字母rwx来表示权限,还可以使用3位数字来表 达文件或目录的权限
		- 读: 4
		- 写:2
		- 执行:1
- chmod命令(change mode)
	- 格式
		- chmod [ugoa] [+-=] [rwx] file/dir 或 chmod nnn file/dir
	- 参数解释
		- u:属主  g:属组  o:其他用户  a:所有用户
		- +:添加权限  -:删除权限  =:赋予权限
		- nnn:三位八进制的权限
	- 常用命令选项
		- -R 递归修改指定目录下的所有子文件及文件夹的权限
		- -f 强制改变文件访问特权;如果是文件的拥有者,则得不到任何错误信息
	- 例子: chmod g+w ll.txt
	- 用数字表示权限(r=4，w=2，x=1，-=0)
		- 例如: chmod  750  b.txt;rwx用二进制表示是111,十进制4+2+1=7
; r-x用二进制表示是101,十进制4+0+1=5
- chown命令
	- 格式:
	- chown 属主 file/dir 
	- chown :属组 file/dir
	- chown 属主:属组 file/dir
	- 常用命令选项
		- -R:递归的修改指定目录下所有文件,子目录的归属

