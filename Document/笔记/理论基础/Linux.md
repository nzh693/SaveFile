#### 1、常用命令

- 杀死进程   kill -s 9+进程号
- 修改文件权限 
- **文件搜索** 

  - **find  / -name file1**																		 从 '/' 开始进入根文件系统搜索文件和目录 

  - **find  / -user user1**                                                                         搜索属于用户 'user1' 的文件和目录 

  - **find  /home/user1 -name \*.bin**                                                在目录 '/ home/user1' 中搜索带有'.bin' 结尾的文件 

  - **find  /usr/bin -type f -atime +100**                                            搜索在过去100天内未被使用过的执行文件 

  - **find  /usr/bin -type f -mtime -10**                                              搜索在10天内被创建或者修改过的文件 

  - **find  / -name \*.rpm -exec chmod 755 '{}' **                             搜索以 '.rpm' 结尾的文件并定义其权限 

  - **find  / -xdev -name \*.rpm**                                                         搜索以 '.rpm' 结尾的文件，忽略光驱、捷盘等可移动设备 

  - **locate \*.ps**                                                                                    寻找以 '.ps' 结尾的文件 - 先运行 'updatedb' 命令 

  - **whereis halt**                                                                                  显示一个二进制文件、源码或man的位置 

  - **which halt**                                                                                       显示一个二进制文件或可执行文件的完整路径

​    

- **用户和群组** 

  - **groupadd group_name**                            											                 创建一个新用户组 

  - **groupdel group_name**                                                                                           删除一个用户组 

  - **groupmod -n  new_group_name  old_group_name**                                       重命名一个用户组 

  - **useradd -c "Name Surname " -g admin -d /home/user1  -s /bin/bash user1**   创建一个属于 "admin" 用户组的用户 

  - **useradd user1**                                                                                                          创建一个新用户 

  - **userdel -r user1**                                                                                                      删除一个用户 ( '-r' 排除主目录) 

  - **usermod -c "User FTP" -g system -d /ftp/user1 -s /bin/nologin user1**    修改用户属性 

  - **passwd**                                                                                                                      修改口令 

  - **passwd user1**                                                                                                          修改一个用户的口令 (只允许root执行) 

  - **chage -E 2005-12-31 user1**                                                                                    设置用户口令的失效期限 

  - **pwck**                                                                                                                           检查 '/etc/passwd' 的文件格式和语法修正以及存在的用户 

  - **grpck**                                                                                                                          检查 '/etc/passwd' 的文件格式和语法修正以及存在的群组 

  - **newgrp group_name**                                                                                              登陆进一个新的群组以改变新创建文件的预设群组 

    

- **YUM 软件包升级器 - （Fedora, RedHat及类似系统）** 

  - **yum install package_name**                                                                  下载并安装一个rpm包

  - **yum localinstall package_name.rpm**                                                  将安装一个rpm包，使用你自己的软件仓库为你解决所有依赖关系 

  - **yum update package_name.rpm**                                                        更新当前系统中所有安装的rpm包

  -  **yum update package_name**                                                               更新一个rpm包 

  - **yum remove package_name**                                                                删除一个rpm包 

  - **yum list**                                                                                                    列出当前系统中安装的所有包 

  - **yum search package_name**                                                                  在rpm仓库中搜寻软件包 

  - **yum clean packages**                                                                              清理rpm缓存删除下载的包 

  - **yum clean headers**                                                                                删除所有头文件 

  - **yum clean all**                                                                                          删除所有缓存的包和头文件

    

- **APT 软件工具 (Debian, Ubuntu 以及类似系统)** 

  - **apt-get install package_name** 															安装/更新一个 deb 包 
  - **apt-cdrom install package_name**                                                      从光盘安装/更新一个 deb 包 
  - **apt-get update**                                                                                     升级列表中的软件包 
  - **apt-get upgrade**                                                                                  升级所有已安装的软件 
  - **apt-get remove package_name**                                                       从系统删除一个deb包
  -  **apt-get check**                                                                                     确认依赖的软件仓库正确
  -  **apt-get clean**                                                                                    从下载的软件包中清理缓存
  -  **apt-cache search searched-package**                                           返回包含所要搜索字符串的软件包名称 

  

  #### 管理使用者和设立权限的命令

  | 命令  | 说明         | 命令    | 说明         |
  | ----- | ------------ | ------- | ------------ |
  | chmod | 用来改变权限 | useradd | 用来增加用户 |
  | su    | 用来修改用户 |         |              |



####     2、Shell/Bash脚本

​       查看脚本解释器： cat /etc/shells

#####        1、变量

```bash
VARIABLE_NAME="Value"
```

​            当命名一个变量是你必须记得以下几点

```bash
    - 变量名是区分大小写的
    - 为了方便，变量名最好大写
    - 要使用变量，必须在变量前面加`$`符号
    - $# 参数个数  $0 脚本名称  $1 脚本第一个参数
    
    #!/bin/bash
    MY_NAME="shellhub"
    echo "Hello, I am $MY_NAME"
    
    #变量赋值给变量
    LIST=$(ls)
    
```

##### 2、if

```bash
#!/bin/bash
if [ $#=1 ]
then
   echo "参数一个";
if
```

​    

