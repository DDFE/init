**感谢那些给我们引到的先驱者们**

###ubuntu sources

1. 首先备份软件源 `cp /etc/apt/sources.list /etc/apt/sources.list_bak`   
2. 然后去 [源地址](http://wiki.ubuntu.org.cn/%E6%BA%90%E5%88%97%E8%A1%A8) 找到对应的源   
3. `sudo gedit /etc/apt/sources.list`将源列表到粘贴源，保存即可
4. sudo apt-get update    
5. 推荐使用 -- 针对13.04
 
		deb http://mirrors.163.com/ubuntu/ raring main restricted universe multiverse
		deb http://mirrors.163.com/ubuntu/ raring-security main restricted universe multiverse
		deb http://mirrors.163.com/ubuntu/ raring-updates main restricted universe multiverse
		deb http://mirrors.163.com/ubuntu/ raring-proposed main restricted universe multiverse
		deb http://mirrors.163.com/ubuntu/ raring-backports main restricted universe multiverse
		deb-src http://mirrors.163.com/ubuntu/ raring main restricted universe multiverse
		deb-src http://mirrors.163.com/ubuntu/ raring-security main restricted universe multiverse
		deb-src http://mirrors.163.com/ubuntu/ raring-updates main restricted universe multiverse
		deb-src http://mirrors.163.com/ubuntu/ raring-proposed main restricted universe multiverse
		deb-src http://mirrors.163.com/ubuntu/ raring-backports main restricted universe multiverse

###常用apt命令：

	sudo apt-get clean 清理所有软件缓存
    apt-cache search package 搜索包 
    apt-cache show package 获取包的相关信息，如说明、大小、版本等 
    sudo apt-get install package 安装包 
    sudo apt-get install package - - reinstall 重新安装包 
    sudo apt-get -f install 修复安装”-f = –fix-missing” 
    sudo apt-get remove package 删除包 
    sudo apt-get remove package - - purge 删除包，包括删除配置文件等 
    sudo apt-get update 更新源 
    sudo apt-get upgrade 更新已安装的包 
    sudo apt-get dist-upgrade 升级系统 
    sudo apt-get dselect-upgrade 使用 dselect 升级 
    apt-cache depends package 了解使用依赖 
    apt-cache rdepends package 是查看该包被哪些包依赖 
    sudo apt-get build-dep package 安装相关的编译环境 
    apt-get source package 下载该包的源代码 
    sudo apt-get clean && sudo apt-get autoclean 清理无用的包 
    sudo apt-get check 检查是否有损坏的依赖
    sudo apt-get autorem‍ove 删除系统不再使用的孤立软件


###chromium [参考地址](http://wiki.ubuntu.org.cn/Chromium%E6%B5%8F%E8%A7%88%E5%99%A8)

	sudo add-apt-repository  ppa:chromium-daily/stable
	sudo apt-get update
	sudo apt-get install chromium-browser


###nodejs

如果不是想使用最新版的特性，还是别编译源码了，直接使用`sudo apt-get install nodejs`就行了
若要自己进行编译安装参照下文，记得将g++,curl,libssl-dev等都安装好否则编译会报错。
[参考地址](http://www.cnblogs.com/smallidea/archive/2012/07/19/2599734.html)
PS：nodejs在github上的 [地址](https://github.com/joyent/node)

	sudo apt-get install nodejs

###npm
*nodejs的包管理器*

    sudo apt-get install npm
    npm -v

###node versions management

	sudo npm install n
	
然后在通过n来安装多个版本的node,[Github](https://github.com/visionmedia/n)下载源码编译安装
n用法简单，详情查看 `n -h`


###php

	sudo apt-get install php5-cli
	php -v
	
###java


1. 不同版本的java
	
	 * default-jre
	 * gcj-4.6-jre-headless
	 * gcj-4.7-jre-headless
	 * openjdk-7-jre-headless
	 * openjdk-6-jre-headless

2. 安装方法 
	
		1. sudo apt-get install openjdk-7-jre-headless
		2. java -version
		
		1. sudo apt-get install openjdk-7-jdk
		2. javac
	
###ruby

	sudo apt-get install ruby1.9.1
	ruby -v
	
###python [参考](http://gichan.iteye.com/blog/1131224)

    1. 查看版本 python -V 
    2. Ubuntu上本身带有python环境，所以不需要重新安装了！
    
###sublime text

    add-apt-repository ppa:webupd8team/sublime-text-2
    apt-get update
    apt-get install sublime-text
    在application里面可以找到sublime－text－2

[参考地址](http://www.cnblogs.com/zhangjun516/archive/2013/01/17/2863957.html)


###sublime text package

	ctrl+` 可以调起控制台 然后将对应的代码ctrl+c/v即可

####sublime2

	import urllib2,os,hashlib; h = '7183a2d3e96f11eeadd761d777e62404' + 'e330c659d4bb41d3bdf022e94cab3cd0'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')
	

####sublime3

	import urllib.request,os,hashlib; h = '7183a2d3e96f11eeadd761d777e62404' + 'e330c659d4bb41d3bdf022e94cab3cd0'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
	

###svn

	sudo apt-get install subversion
	svn --version
	

###vpn

	1. install
	sudo apt-get install openvpn
	openvpn --version 
	openvpn --config didi.ovpn (didi.ovpn文件路径即可)
	PS：host连接上VPN后，guest可以不用连了，前提是host跟guest是桥接的链接方式
	
	2. 整个过程如下
	parallels@ubuntu:~$ sudo openvpn --config didi.ovpn 
	Thu May 15 22:14:55 2014 OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Feb 13 2013
	Enter Auth Username:liujiangbei
	Enter Auth Password:
	Thu May 15 22:15:00 2014 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
	Thu May 15 22:15:00 2014 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
	Thu May 15 22:15:00 2014 LZO compression initialized
	Thu May 15 22:15:00 2014 UDPv4 link local (bound): [undef]
	Thu May 15 22:15:00 2014 UDPv4 link remote: [AF_INET]118.244.193.172:1194
	Thu May 15 22:15:00 2014 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
	Thu May 15 22:15:00 2014 [jx] Peer Connection Initiated with [AF_INET]118.244.193.172:1194
	Thu May 15 22:15:03 2014 TUN/TAP device tun0 opened
	Thu May 15 22:15:03 2014 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
	Thu May 15 22:15:03 2014 /sbin/ifconfig tun0 10.8.0.34 pointopoint 10.8.0.33 mtu 1500
	Thu May 15 22:15:03 2014 Initialization Sequence Completed

###git

      sudo apt-get install git-core
      git --version

###Git与Github

1. 生成ssh-key `sudo ssh-keygen -t rsa -C "my first ssh-key` [参考地址](http://blog.csdn.net/alex_my/article/details/8741625)    
2. 使用vi命令查看生成的ssh_key.pub内容并复制添加到Github上面的SSH Key里面    
3. 测试一下本地git跟github是否连接    
	
		ssh git@github.com 会提示输入密码，也就是生成的ssh_key的密码，整个过程如下：
	
		parallels@ubuntu:~$ ssh git@github.com
		The authenticity of host 'github.com (192.30.252.130)' can't be established.
		RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
		Are you sure you want to continue connecting (yes/no)? yes
		Warning: Permanently added 'github.com,192.30.252.130' (RSA) to the list of known hosts.
		PTY allocation request failed on channel 0
		Hi liujb! You've successfully authenticated, but GitHub does not provide shell access.
		Connection to github.com closed.
			
	[参考地址](http://blog.csdn.net/alex_my/article/details/8741615)
	
###screen shots

`sudo ape-get install scrot`[参考地址](http://blog.csdn.net/supercrsky/article/details/8472800)
使用方法：

	1. 按住print screen能截整个桌面
	2. Alt+Print Screen能截活动窗口，但还是不功能不行

###dictionary

[参考地址](http://linux.ctocio.com.cn/59/12422559.shtml)     

	1）安装软件：    
	2）解压下载的文件包：sudo tar -xjvf stardict-oxford-gb-2.4.2.tar.bz2    
	3）移动文件：sudo mv stardict-oxford-gb-2.4.2 /usr/share/stardict/dic/     

###文本编辑软件

	nano新手适合   
	vi    
	vim    
	gedit   
	kwrite   

vim的不同种类
	
 * vim
 * vim-gnome
 * vim-tiny
 * vim-athena
 * vim-gtk
 * vim-nox

###Eclipse

[参考地址](http://hi.baidu.com/sanwer/item/e5328bcdf2beaa27a1b50a0f)


###常用软件推荐 [参考地址](http://ben-lab.com/tech/1765.html)

###安装QQ [参考地址](http://blog.ubuntusoft.com/ubuntu-qq.html)


###解压tar.gz文件

	tar xzf xx.tar.gz

###中文输入法

*以为一定要先安装中文语言包，中文语言包死活安装不上，不知道什么原因，最后找到 [参考地址](http://wiki.ubuntu.org.cn/IBus)* 问题得到解决!


###wiznote

- 推荐使用通过添加软件源的方式去安装
	 
		$ sudo add-apt-repository ppa:wiznote-team    
		$ sudo apt-get update    
		$ sudo apt-get install wiznote    

- 或者直接下载wiz官方的tar.gz文件解压即可 tar zxvf filename.tar.gz [参考地址](http://www.cnblogs.com/eoiioe/archive/2008/09/20/1294681.html)

###use gnome and remove unity desktop


1. ubuntu 12.04 中安装gnome桌面的命令为：     
`sudo apt-get install gnome-session-fallback`
或者    
`sudo apt-get install gnome-panel`

2. 安装好gnome桌面后注销重新登录，在用户名右边有一个图标，可以选择使用进入的桌面，我选择了gnome classic，然后就可以重返经典的gnome桌面了。
3. 在删除unity桌面之前，要把ubuntu默认的登录界面也改为gnome，命令如下：    
`sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic`
这是设置登录界面为 gnome classic的，如果你喜欢gnome3，则用：    
`sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell`

4. 接下来就可以卸载unity了。
	 
		sudo apt-get -y –auto-remove purge unity
		sudo apt-get -y –auto-remove purge unity-commonp
		sudo apt-get -y –auto-remove purge unity-lens*
		sudo apt-get -y –auto-remove purge unity-services
		sudo apt-get -y –auto-remove purge unity-asset-pool

###ssh client and server [reference](http://blog.csdn.net/netwalk/article/details/12952051)
