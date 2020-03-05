# Linux-jdk-redis
linux下安装jdk和redis的配置


安装JDK：
1.下载完成后，使用Xftp软件上传到Linux服务器上：/usr/local/java
执行命令：tar -zxvf  jdk-8u66-linux-x64.tar.gz  解压
2.配置环境变量
修改/etc/profile文件，执行命令：vi/etc/profile

export JAVA_HOME=/usr/local/software/jdk1.8.0_66

export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

export PATH=$JAVA_HOME/bin:$PATH

执行命令：source /etc/profile     刷新环境变量

3.验证环境变量
java- version 和 javac -version

连接：https://blog.csdn.net/xiaoguanyusb/article/details/82745067


redis安装启动：
1.上传源码包到linux服务器 /usr/local/
解压源码：tar -zxvf redis-3.0.0.tar.gz
2.进入解压后的目录中  make PREFIX=/usr/local/redis install进行安装
3.安装完后会在/usr/local/redis-3.0.0下出现一个bin目录，bin目录中就是我们要使用的内容
4，启动redis服务
前端模式启动服务端：./redis-server
前端模式启动的缺点是ssh命令窗口关闭则redis-server程序结束

后端模式启动服务端
启动后自动在后台运行，与ssh窗口是否关闭无关（需要配置）
将redis.conf配置文件拷贝到bin目录下，切换到bin目录下
由于配置文件中默认为前端模式启动，需手动编辑修改配置文件中内容：vi redis.conf   按pgDn向下翻找到daemonize no改为yes
进行后端模式启动：./redis-server redis.conf
然后查看是否成功启动服务：ps -aux|grep redis

连接：https://blog.csdn.net/huangyuhuangyu/article/details/80263525
