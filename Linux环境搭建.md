#### ubuntu��������

> Ubuntu�汾19.10
>
> ��һ���ֿ��������
>
> �ڶ�����windows���������װ

--------

1. github��װ

   - `sudo apt-get install git`
   - `git config --global user.name "your name"`
   - `git config --global user.email "your _email@youremail.com"`
   - `ssh-keygen -t rsa -C "your_email@your email.com"`֮�����~/������.ssh�ļ���
   - `cat ~/.ssh/id_rsa.pub`����key�������뵽github�Լ��ֿ��ssh key��
   - `ssh -T git@github`��֤�Ƿ�ɹ�

2. vim��װ

   - `sudo apt-get install vim`

   - `git clone git@github.com:shengfzy/Vim-config.git`���ҵ�.vimrc�����ļ�clone������

   - `vim ~/.vimrc`������´��룺

     `source Vim-config·��/Vim-config/.vimrc`

   - ��װVundle

     - `mkdir -P ~/.vim/bundle/Vundle`
     - `cd ~/.vim/bundle/Vundle`
     - `git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim`

   - ����vim ����:PluginInstall��װvim������������.vimrc�����

3. ~~��װvmware-tools��������Ҫ��������~~

   - ~~����ʹ������ķֱ������Ŵ��ڵĵ������仯~~
   - ~~���������ɵ���windows�������֮���ƶ�~~

4. ����FTP���񣬷����windowsϵͳ�����ļ���

   - windows�����ذ�װFilezilla��ע���ǿͻ���client�汾��

   - ubuntu�°�װvsftpd
     1. ��װ�����sudo apt-get install vsftpd
     2. ���������ļ���sudo vim /etc/vsftpd.conf
     3. ��vim�򿪺�
        `Local_enable=YES`
        `write_enable=YES`
        ����ǰ��ע��ȥ���������˳�
     4. ��������sudo /etc/init.d/vsftpd restart

5. NFS������
   - sudo apt-get install nfs-kernel-server rpcbind
   - ����nfs��
     1. sudo vim /etc/exports
     2. ���ļ������ӣ�/home/matteo/linux/nfs *(rw,sync,no_root_squash)
     3. sudo /etc/init.d/nfs-kernel-server restart

6. SSH������

   - sudo apt-get install openssh-server

7. ������빤�߰�װ
   - sudo mkdir /usr/local/arm
   - sudo cp gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf.tar.xz /usr/local/arm -f
   - cd /usr/local/arm
   - sudo tar -vxf gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf.tar.xz
   - sudo vim /etc/profile
   - ���ļ�������룺export PATH=$PATH:/usr/local/arm/gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf/bin

8. ��װ��ؿ��ļ�
   - sudo apt-get install lsb-core lib32stdc++6
   - �����������֤��arm-linux-gnueabihf-gcc -v

9. vscode��װ

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
   - DeviceTree����
   - Python
   - Python Snippets

10. windows�����ذ�װXshell���ڵ������������������ҪӦΪ�����濴�������

11. CH340����оƬ������װ

    - linux �ں˰汾2.6�����Դ���CH340оƬ

---

1. ��װdeepin-wine

   - `git clone https://gitee.com/wszqkzqk/deepin-wine-for-ubuntu.git`

   - ����git�ֿ�ִ��`./install.sh`

   - ��ȡ΢������

     ```
   wget https://mirrors.aliyun.com/deepin/pool/non-free/d/deepin.com.wechat/deepin.com.wechat_2.6.2.31deepin0_i386.deb      
     ```

   - ��װ΢��

     `sudo dpkg -i deepin.com.wechat_2.6.2.31deepin0_i386.deb`

2. �ٶ�����
   
   - ����ֱ���ṩdeb������װ����
3. office�칫���
   
   - wps�����ṩlinux�汾����װ����