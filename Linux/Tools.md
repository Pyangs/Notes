##### 任务管理器
    $ gnome-system-monitor

##### root 权限文件管理器
    $  sudo nautilus

##### GRUB
    $ gedit /etc/default/grub
    # If you change this file, run 'sudo update-grub'

##### 使用grub-customizer来编辑GRUB
    $ sudo add-apt-repository ppa:danielrichter2007/grub-customizer
    $ sudo apt-get update
    $ sudo apt-get  install grub-customizer

##### sublime 不能输入中文的解决方法
    $ git clone https://github.com/lyfeyaj/sublime-text-imfix.git
    $ cd sublime-text-imfix
    $ ./sublime-imfix

##### solve 'E: 无法定位软件包 xxxx' 
    # checkout to a usable soft source first
    $ sudo apt-get update
