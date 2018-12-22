<h3>flask环境配置</h3>

[1. 前言](#content1)

[2. OSX环境配置](#content2)

　　[2.1 安装python/虚拟环境/flask](#content21)
  
　　[2.2 安装MySQL/pymysql/SQLAlchemy](#content22)
  
[3. windows环境配置](#windows)

　　[3.1 安装python/虚拟环境/flask](#content31)
  
　　[3.2 安装MySQL/pymysql/SQLAlchemy](#content32)
  

<span id='content1'><h5>前言</h5></span>
使用pycharm作为ide开发, ide在创建工程时会帮你建立虚拟环境/flask环境等, 否则需要自己配置开发环境
<span id='content2'><h5>osx环境配置</h5></span>
<span id='content21'><h6>(一)python / 虚拟环境 / flask</h6></span>
1. 安装python3.7
2. 安装virtualenv
```
pip3 install virtualenv
```
3. 之后创建一个目录 用来存放所有的虚拟环境
```
mkdir ~/venvs
cd venvs
```
4. 在该目录下创建一个新的虚拟环境
```	
Reid:~ ReidWang$ which python3					//首先找到python3的安装路径
>>/Library/Frameworks/Python.framework/Versions/3.7/bin/python3
virtualenv -p  /Library/Frameworks/Python.framework/Versions/3.7/bin/python3 flaskEnv 
```
5. 激活虚拟环境
```
source flaskEnv/bin/activate
```
虚拟环境激活后所有的包安装更新的操作都是在该虚拟环境下进行, 这样不同版本的python, 不同版本的第三方包之间就不会造成影响
比如在虚拟环境下安装flask, 激活虚拟环境后
```
pip3 install Flask
```
即可完成安装
之后再终端查看对应的虚拟环境的flask安装情况

其他指令:
退出当前虚拟环境： deactivate  
切换到其它环境： workon 环境名称
删除环境： rmvirtualenv 环境名称  
如果使用pycharm的话, 在创建project的时候IDE会帮你创建新的虚拟环境以及下载flask等相依赖包, 无需自己操作

<span id='content22'><h6>(二)MySQL / pymysql / SQLAlchemy</h6></span>
官网下载安装文件, 安装完成后在系统偏好设置中启动mysqlserver服务
安装过程中需要设置root密码
启用mysql命令时候报错:
-bash: mysql: command not found
这是路径错误的原因, 终端直接查找的是usr/local/bin下边的命令, 我们需要把mysql的命令放到.bash_profile中
vim ~/.bash_profile
添加：
export PATH=$PATH:/usr/local/mysql/bin
保存，退出
重新启动（加载）bash_profile文件
source ~/.bash_profile
终端启动mysql命令
mysql -u root -p
之后安装数据库连接组件pymysql
pip3 install pymysql
使用Flask-SQLAlchemy管理数据库
Flask-SQLAlchemy是一个Flask扩展，它简化了在Flask应用程序中对SQLAlchemy的使用。SQLAlchemy是一个强大的关系数据库框架，支持一些数据库后端。提供高级的ORM(object relationship mapping 模型关系映射)和底层访问数据库的本地SQL功能
pip3 install flask-sqlalchemy

<span id='content3'><h5>windows环境配置</h5></span>
<span id='content31'><h6>(一)python / 虚拟环境 / flask</h6></span>
1. 下载python3的安装包, 安装时候选择addpath, 会自动帮你添加环境变量, 安装好后打开cmd输入python, 如果提示不是内部或外部命令, 则有可能需要重启或重新手动添加环境变量
2. 安装virtualenv  pip3 install virtualenv
安装完成后新建一个目录用来存储所有的虚拟环境 mkdir venvs 
3. 创建虚拟环境
首先找到python的安装目录: where python
C:\Users\Administrator\AppData\Local\Programs\Python\Python37\python.exe
之后执行:
virtualenv -p  C:\Users\Administrator\AppData\Local\Programs\Python\Python37\python.exe 环境名   即可
4.激活虚拟环境
进入到新建的虚拟环境下  E:\venvs>cd firflask
之后执行 E:\venvs\firflask>Scripts\activate  即可
5.虚拟环境下安装flask   pip3 install Flask
安装完成后进入python解释器查看flask是否安装成功
<span id='content32'><h6>(二)MySQL / pymysql / SQLAlchemy</h6></span>
安装MySQL  (zip压缩包方式安装, 版本8.0.13)
镜像: http://mirrors.163.com/mysql/Downloads/MySQL-8.0/mysql-8.0.13-winx64.zip
下载mysql压缩包 解压到相应目录(目录中不要有空格或中文)
1.写配置文件my.ini
在根目录下新建my.ini文件, 文件中基本内容如下:
[mysql]
设置mysql客户端默认字符集
default-character-set=utf8mb4
[mysqld]
设置3306端口
port=3306
设置mysql的安装目录
basedir=D:\\develop\\software\\mysql-8.0.13-winx64
允许最大连接数
max_connections=20
服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8mb4
创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
2.初始化mysql  管理员权限运行cmd, 进入mysql解压的目录
解压目录/bin目录下  执行  mysqld --initialize --console   会自动生成临时root密码
初始化完成后:
注册mysql服务    mysqld install
启动mysql    net start mysql
登录mysql    mysql -uroot -p  第一次登陆通过临时密码
之后修改root密码
ALTER USER USER() IDENTIFIED BY '新密码';
到此mysql安装和启动完成 之后每次需要启动mysql服务只需进入bin目录, 
执行启动    net start mysql    以及登陆    mysql -uroot -p 


(三)flask-script
进入虚拟环境后下执行:    
pip3 install flask-script

(四) WTForms
进入虚拟环境后执行:
pip3 install flask-wtf
