##### See http://blog.csdn.net/mbxc816/article/details/7473906

##### apt简单的来说，就是给Ubuntu安装软件的一种命令方式。
##### 一、apt的相关文件
	/etc/apt/sources.list 	设置软件包的获取来源
	/etc/apt/apt.conf 	apt配置文件
	/etc/apt/apt.conf.d/ 	apt的零碎配置文件
	/etc/apt/preferences 	版本参数
	/var/cache/apt/archives/ 	存放已经下载的软件包
	/var/cache/apt/archives/partial 	存放正在下载的软件包
	/var/lib/apt/lists/ 	存放已经下载的软件包详细信息
	/var/lib/apt/lists/partial/ 	存放正在下载的软件包详细信息
##### 二、apt-get命令的子命令
	update 	更新软件包列表
	upgrade 	升级系统中的所有软件包
	install 	安装软件包
	remove 	卸载软件包
	autoremove 	仅删除不需要再次下载的软件包
	purge 	彻底删除软件包（包括配置文件）
	source 	下载源代码
	build-dep 	自动下载安装编译某个软件所需要的软件包
	dist-upgrade 	升级整个发行版
	dselect-upgrade 	安装dselect的选择进行升级
	clean 	删除本地缓存的所有升级包
	autoclean 	删除本地缓存中无用的软件包
	check 	检查是否存在有问题的依赖关系
	例:$ sudo apt-get install php5-mysql apache2

	$ sudo apt-get update && sudo apt-get upgrade
##### 三、apt-get命令选项
	-d,--download-only 	仅下载，不安装
	-f,--fix-broken 	修复依赖问题（用于install和remove子命令）
	-m,--ignore-missing,--fix-missing 	忽略缺失的软件包。遇到无法下载的软件包，自动忽略
	--no-download 	禁止下载软件包。与-m配合，可以使apt只使用已经下载的软件包
	-q,--quiet 	静默模式，输出的信息适合做日志
	-s,--simulate,--just-print 	模拟测试，不做出实际操作，不改变系统
	-y,--yes,--assume-yes 	在系统提问时，自动应答yes
	-u,--show-upgraded 	显示已升级的软件包
	-V,--verbose-versions 	显示已安装和已升级的软件包的完整版本号
	-b,--compile,--build 	在源码包下载完成后进行编译
	--ignore-hold 	忽略被保留的软件包
	--no-upgrade 	不要升级软件包
	--force-yes 	强制回答yes
	--print-uris 	仅答应软件包地址，不安装
	--purge 	彻底删除，包括配置文件
	--reinstall 	重新安装软件包

##### 四、apt-cache命令
	功能：搜索某个软件包的名字或显示某个软件包的详细信息
	搜索mysql的软件包 	$ apt-cache search mysql
	查看ssh软件包的详细版本号 	$ apt-cache show ssh

##### 五、Red Hat、Fedora和Ubuntu软件包操作对比
	任务 	Red Hat、Fedora 	Ubuntu
	基本信息
	软件包后缀 	*.rpm 	*.deb
	软件源配置文件 	/etc/yum.conf 	/etc/apt/sources.list
	安装、删除、升级软件包
	更新软件包列表 	每次运行yum时自动执行 	apt-get update
	从软件仓库软件安装软件 	yum install package 	apt-get install package
	安装一个已下载的软件包 	yum install pkg.rpm

	rpm -i pkg.rpm
		dpkg -i pkg.deb

	pkg --install pkg.deb
	删除软件包 	rpm -e package 	apt-get remove package
	软件包升级检查/测试 	yum check-update 	apt-get -s upgrade

	apt-get -s dist-upgrade
	升级软件包 	yum update

	rpm -Uvh [args]
		apt-get upgrade
	升级整个系统 	yum upgrade 	apt-get dist-upgrade
	软件包信息
	获取某软件包的信息 	yum search package 	apt-cache show package
	获取所有软件包的信息 	yum list available 	apt-cache dumpavail
	显示所有已安装的软件 	yum list installed

	rpm -qa
		dpkg -l

	dpkg --list
	获取某个已安装软件包的信息 	yum info package

	rpm -qi package
		dpkg --status package
	列出某个已安装软件包所包含的文件列表 	rpm -ql package 	 
	列出某个已安装软件包所包含的文档 	rpm -qd package 	无
	列出某个已安装软件包所包含的配置文件 	rpm -qc package 	无
	显示某个软件包所依赖的软件包列表 	rpm -qR package 	apt-cache depends package
	显示某个软件包的反向依赖关系 	rpm -q -whatrequires [args] 	apt-cache rdepends package
	软件包文件信息
	获取某个软件包文件的信息 	rpm -qpi pkg.rpm 	dpkg --info pkg.deb
	获取某个软件包文件所包含的文件列表 	rpm -qpl pkg.rpm 	dpkg --contents pkg.deb
	获取某个软件包文件所包含的文档 	rpm -qpd pkg.rpm 	无
	获取某个软件包文件所包含的配置文件 	rpm -qpc pkg.rpm 	无
	软件包解压 	rpm2cpio pkg.rpm | cpio -vid 	dpkg-deb --extract pkg.deb
	搜索某个文件是由哪个软件包安装的 	rpm -qf /file/name 	dpkg -S /file/name

	dpkg --search /file/name
	搜索所有提供某个文件的软件包 	yum provides /file/name 	apt-file search /file/name
	杂项
	显示本地软件包缓存的状态 	无 	apt-cache stats
	校验所有已安装的软件包 	rpm -Va 	debsums
	删除本地缓存的所有软件包 	yum clean packages 	apt-get clean
	仅删除本地缓存中过时的软件包 	无 	apt-get autoclean
	删除所有软件包信息 	yum clean headers 	apt-file purge