---
layout: default
---

# MySQL基本命令操作
2015.06.13

### 1.基本操作

Mysql的所有命令末尾都需要以分号结束，一条命令可以分成多行书写。

+ 连接数据库：mysql –u root –p；
+ 查看所有数据库：show databases;
+ 创建数据库：create database databaeName;
+ 选择数据库：use databaseName;只有选择数据库后才能进行相关的数据库操作。
+ 删除数据库：drop database databaseName;
+ 创建表：create table use( id varchar(10) primary key, name varchar(10) not null);
+ 查看所有表：show tables;
+ 删除表：drop table tableName;

### 2.字符集

MySQL在安装时字符集默认是latin，不支持中文。这在实际开发过程中会带来很大的问题，所以一般需要将字符集方式修改为utf8。在windows中安装时可以选择默认的字符集为utf8，但在linux下直接使用命令安装是不能选择的，而且linux下修改字符集的方式比较复杂（试过几次都遇到问题）。个人觉得可以尝试转码的方式，类似Java中URLEncoder和URLDecoder方法、Hbase中存数据的Bytes.toBytes方法等，这样就不会有乱码的问题，不足之处是编码与解码需要消耗时间。

### 3.最基本vi操作

虽然图形化用户界面修改文件很方便，但有些时候必须通过vi来修改，无奈vi虽然强大，却也复杂。非常基本的几条vi命令，以后要用再学吧。

vi有三种状态：input mode，command mode和line mode。

1. 进入文件：vi filename；
2. 初入vi时，自动在command mode，按i由command mode进入input mode；
3. 在input mode，和正常文件修改一样；
4. 修改完毕后，按Esc返回到command mode；
5. 输入ZZ存档并退出vi，如果中途发生意外，可以通过命令:q!强制离开（不保存任何修改）。