#### ubuntu环境配置

> Ubuntu版本19.10
>
> 第一部分开发环境搭建
>
> 第二部分windows常用软件安装

--------

1. github安装

   - `sudo apt-get install git`
   - `git config --global user.name "your name"`
   - `git config --global user.email "your _email@youremail.com"`
   - `ssh-keygen -t rsa -C "your_email@your email.com"`之后会在~/下生成.ssh文件夹
   - `cat ~/.ssh/id_rsa.pub`复制key，并加入到github自己仓库的ssh key中
   - `ssh -T git@github`验证是否成功

2. vim安装

   - `sudo apt-get install vim`

   - `git clone git@github.com:shengfzy/Vim-config.git`将我的.vimrc配置文件clone到本地

   - `vim ~/.vimrc`添加如下代码：

     `source Vim-config路径/Vim-config/.vimrc`

   - 安装Vundle

     - `mkdir -P ~/.vim/bundle/Vundle`
     - `cd ~/.vim/bundle/Vundle`
     - `git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim`

   - 进入vim 输入:PluginInstall安装vim插件，插件可在.vimrc中添加

3. ~~安装vmware-tools，作用主要有两个：~~

   - ~~可以使虚拟机的分辨率随着窗口的调整而变化~~
   - ~~鼠标可以自由的在windows和虚拟机之间移动~~

4. 开启FTP服务，方便和windows系统互传文件：

   - windows下下载安装Filezilla（注意是客户端client版本）

   - ubuntu下安装vsftpd
     1. 安装软件：sudo apt-get install vsftpd
     2. 更改配置文件：sudo vim /etc/vsftpd.conf
     3. 用vim打开后将
        `Local_enable=YES`
        `write_enable=YES`
        两行前的注释去掉，保存退出
     4. 重启服务：sudo /etc/init.d/vsftpd restart

5. NFS服务开启
   - sudo apt-get install nfs-kernel-server rpcbind
   - 配置nfs：
     1. sudo vim /etc/exports
     2. 在文件最后添加：/home/matteo/linux/nfs *(rw,sync,no_root_squash)
     3. sudo /etc/init.d/nfs-kernel-server restart

6. SSH服务开启

   - sudo apt-get install openssh-server

7. 交叉编译工具安装
   - sudo mkdir /usr/local/arm
   - sudo cp gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf.tar.xz /usr/local/arm -f
   - cd /usr/local/arm
   - sudo tar -vxf gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf.tar.xz
   - sudo vim /etc/profile
   - 在文件最后输入：export PATH=$PATH:/usr/local/arm/gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf/bin

8. 安装相关库文件
   - sudo apt-get install lsb-core lib32stdc++6
   - 交叉编译器验证：arm-linux-gnueabihf-gcc -v

9. vscode安装

   - c/c++
   - c/c++ Snippets
   - c/c++ Advanced Lint
   - Code Runner
   - Include AutoComplete
   - Rainbow Brackets
   - GBKtoUTF8
   - ARM
   - vscode-icons
   - compareit
   - DeviceTree即可
   - Python
   - Python Snippets
   - Local History
   - Todo Tree
   - Better Comments
   - Better Align
   - change-case

10. windows下下载安装Xshell串口调试软件，用这个软件主要应为它界面看着贼舒服

11. CH340串口芯片驱动安装

    - linux 内核版本2.6以上自带了CH340芯片

---

~~1. 安装deepin-wine~~

   ~~- `git clone https://gitee.com/wszqkzqk/deepin-wine-for-ubuntu.git`~~

   ~~- 进入git仓库执行`./install.sh`~~

   ~~- 获取微信容器~~

   ~~```~~
   ~~wget https://mirrors.aliyun.com/deepin/pool/non-free/d/deepin.com.wechat/deepin.com.wechat_2.6.2.31deepin0_i386.deb      
   ~~```~~

   ~~- 安装微信~~

   ~~`sudo dpkg -i deepin.com.wechat_2.6.2.31deepin0_i386.deb`~~

2. 百度网盘
   
   - 官网直接提供deb包，安装即可
3. office办公软件
   
   - wps官网提供linux版本，安装即可
