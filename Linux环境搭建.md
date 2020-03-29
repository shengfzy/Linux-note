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

   - 安装vim-plug(用来替代Vundle)
       ```bash
     - curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
     ```
     
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
     
   - uboot中使用的NFS版本为V2版本，而ubuntu中版本为V3,V4及以上版本，需要让ubuntu兼容V2版本, 否则在下载文件的时候会产生***ERROR:File lookup fail
   
   - sudo vim /etc/default/nfs-kernel-server
   
     ```bash
     RPCNFSDCOUNT = '-V 2 8'
     RPCMOUNTDOPTS="-V 2 --manage-gids"
     RPCNFSDOPTS="--nfs-version 2,3,4 --debug --syslog"
     ```
   
   - sudo service nfs-kernel-server restart

6. TFTP服务器

   - sudo apt-get install tftp-hpa tftpd-hpa

   - 配置:

     1. vim /etc/xinetd.d/tftp

     2. 输入如下内容

        ```c
        server tftp
        {
         socket_type = dgram
         protocol = udp
         wait = yes
         user = root
         server = /usr/sbin/in.tftpd
         server_args = -s /home/zuozhongkai/linux/tftpboot/
         disable = no
         per_source = 11
         cps = 100 2
         flags = IPv4
        }
        ```

     3. sudo service tftpd-hpa start

     4. vim /etc/default/tftpd-hpa

     5. 输入以下内容

        ```bash
        # /etc/default/tftpd-hpa
        
        TFTP_USERNAME="tftp"
        TFTP_DIRECTORY="/home/matteo/linux/tftpboot"
        TFTP_ADDRESS=":69"
        TFTP_OPTIONS="-l -c -s"
        ```

     6. sudo service tftpd-hpa restart

7. SSH服务开启

   - sudo apt-get install openssh-server

8. 交叉编译工具安装
   - sudo mkdir /usr/local/arm
   - sudo cp gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf.tar.xz /usr/local/arm -f
   - cd /usr/local/arm
   - sudo tar -vxf gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf.tar.xz
   - sudo vim /etc/profile
   - 在文件最后输入：export PATH=$PATH:/usr/local/arm/gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf/bin

9. 安装相关库文件
   - sudo apt-get install lsb-core lib32stdc++6
   - 交叉编译器验证：arm-linux-gnueabihf-gcc -v

10. vscode安装

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

11. windows下下载安装Xshell串口调试软件，用这个软件主要应为它界面看着贼舒服

12. CH340串口芯片驱动安装

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

1. 安装Docker版沙盒微信

   - 安装Docker

     1. 卸载旧版本Docker-engine

        ```bash
        $ sudo apt-get remove docker \
        							   docker-engine \
        							   docker.io
        ```

     2. 使用脚本安装docker

        ```bash
        $ curl -fsSL get.docker.com -o get-docker.sh
        $ sudo sh get-docker.sh --mirror Aliyun
        # $ sudo sh get-docker.sh --mirror AzureChinaCloud
        ```

     3. 启动Docker CE

        ```bash
        $ sudo systemctl enable docker
        $ sudo systemctl start docker
        ```

     4. 建立docker用户组

        ```bash
        $ sudo groupadd docker
        $ sudo usermod -aG ${USER} docker
        $ sudo service docker restart
        ```

     5. 测试是否安装正确

        ```bash
        $ docker run hello-world
        ```

     6. 镜像加速

        ```bash
        $ sudo vim /etc/docker/daemon.json
        {
        	"registry-mirrors": [
        		"https://dockerhub.azk8s.cn",
        		"https://hub-mirror.c.163.com"
        	]
        }
        ```

        之后重启服务

        ```bash
        $ sudo systemctl daemon-reload
        $ sudo systemctl restart docker
        ```

     7. 安装沙盒微信

        ```bash
        curl -sL https://raw.githubusercontent.com/huan/docker-wechat/master/dochat.sh | bash
        ```

2. 安装google输入法：

   1. 在ubuntu商店上安装fcitx及相关组件
   2. sudo apt-get install fcitx-googlepinyin

3. 百度网盘

   - 官网直接提供deb包，安装即可

4. office办公软件

   - wps官网提供linux版本，安装即可