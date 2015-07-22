##linux\svn\git\mysql等常用命令使用记录

[svn命令详解](http://blog.csdn.net/wklken/article/details/6594956)    
[vi命令详解](http://www.cnblogs.com/88999660/articles/1581524.html)     
[git命令详解](http://blog.csdn.net/ithomer/article/details/7529022)     
[源码安装nginx](http://www.nginx.cn/install)    



###一、svn命令

####基础

----

1. `svn list svn://10.10.10.60/xiaoju/server/static/` -- show list
2. `svn co svn://10.10.10.60/xiaoju/server/trunk/api/v2/views` -- checkout
3. `svn add xx` -- add files or folders
4. `svn import $DIR $URL -m “Something your want to mark.”` -- import local folder to svn and commit to remote
4. `svn rm file` -- remove
5. `svn mv old_file new_file` -- move or rename
5. `svn up` -- update
3. `svn ci  filename -m "checkin note”` -- checkin
4. `svn st -v/-u` -- show status
5. `svn log filename` -- show logs
6. `svn cat -r 10528 home.html ` -- show history 
6. `svn delete filename` -- delete
13. `svn delete –force over-there` -- force to delete


####进阶

----

1. `svn export svn://10.10.10.60/xiaoju/server/trunk/api/v2/views` -- use for release project, without .svn folder
8. `svn diff -r 12302:12304 home.html` -- diff two files
2. `svn diff filename` -- show difference from the working file and the latest version
2. `svn diff get_hb_list.tpl |vim -R -` -- use vim to diff two files
4. `svn diff filename -r1234:2345[|vim -R -]` -- use vim to diff two files
3. `svn up –r 200 file.c` -- 将本地的file.c还原为200版本，【本地是拿下来了，版本库端并没有改变】
1. `svn mkdir newdir`
1. `svn mkdir newdir -m "Making a new dir" svn://10.10.10.60/xiaoju/server/`
20. svn resolve --accept working compressed，svn revert compressed－－解决目录compressed树冲突
22. svn revert filename
22. 冲突的解决方法：
  
		1. 先将.mine文件拷贝到你自己的文件
		2. 先跟test.html跟低版本的比较
		3. 再将test.html跟高版本的比较
		4. 解决完冲突之后再diff一下
		5. 然后设置svn resolved test.html
		6. 然后ci
		
23. ci的时候出现 xx.html is out of date－－解决方法就是先update一下，然后再ci  


###二、Linux命令（常用）

####1. 基础

----

1. ls
2. cp
4. mv
5. scp
6. rm				    
1. `scp  -r  $DIR $DIR` -- scp -r 113.11.197.199:~/app/api/v2/views/webapp/home.html . 12505cp -r 
2. `tar xvf filename.tar` -- 解包（tar是打包不是压缩）
3. `tar cvf filename.tar DIRNAME` -- 打包
4. `gunzip gilename.gz` -- 解压gz文件
5. `gzip -d filename.gz` -- 解压文件
6. `gzip filename` -- 压缩为filename.gz
7. `tar zxvf filename.tar.gz` -- 解压.tar.gz并解包
8. `tar zcvf filename.tar.gz DIRNAME` -- 打包文件夹并压缩为tar.gz
9. `du -sh f-weixin-sug` -- 查看文件夹占用的磁盘空间



####2. 进阶

1. hostname－－显示主机名
2. top－－显示进程
3. tail -f /home/xiaoju/php/logs/v2/didi.log.wf  |grep wxtransaction -A10 —color
4. curl
5. wget
6. 安装wget的方法

		1. curl -O http://ftp.gnu.org/gnu/wget/wget-1.13.4.tar.gz
		2. tar -xzvf wget-1.13.4.tar.gz
		3. cd wget-1.13.4
		4. ./configure --with-ssl=openssl
		5. make
		6. sudo make install

7. ifconfig en0     
8. ping ifconfig.me
8. curl ifconfig.me
9. ps -ef |grep packagename
10. kill pid
11. grep的详细使用

	
	

###三、git -- Linux & mac

####1. 安装和配置

**Install:**

      sudo apt-get install git-core
      git --version

**Setting** [参考地址](http://blog.csdn.net/alex_my/article/details/8741615)

1. 生成ssh-key `sudo ssh-keygen -t rsa -C "my first ssh-key` [参考地址](http://blog.csdn.net/alex_my/article/details/8741625)    
2. 使用vi命令查看生成的ssh_key.pub内容并复制添加到Github上面的SSH Key里面    
3. 测试一下本地git跟github是否连接    
	
		ssh git@github.com 会提示输入密码，也就是生成的ssh_key的密码，整个过程如下：
	
		parallels@ubuntu:~$ ssh git@github.com		The authenticity of host 'github.com (192.30.252.130)' can't be established.		RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.		Are you sure you want to continue connecting (yes/no)? yes		Warning: Permanently added 'github.com,192.30.252.130' (RSA) to the list of known hosts.		PTY allocation request failed on channel 0		Hi liujb! You've successfully authenticated, but GitHub does not provide shell access.		Connection to github.com closed.
			
####2. Create a new repository on the command line

    touch README.md
    git init
    git add README.md
    git commit -m "first commit"
    git remote add origin git@github.com:liujb/c-study.git
    git push -u origin master
    
####3. Push an existing repository from the command line

    git remote add origin git@github.com:liujb/c-study.git
    git push -u origin master
    

####4. Basic command

1. `git clone git@github.com:liujb/didi-fe.git`
2. `git status`
3. `git add file`
4. `git rm file`
5. `git commit file -m "These is comment"`
6. `git pull origin master`
6. `git push origin master`
7. `git branch f-test-branch master` -- 从master分支创建分支
8. `git checkout f-test-branch` -- 切换到f-test-branch分支
8. `git branch` -- 查看分支 
7. `git checkout -b f-test-branch master` -- 创建分支并切换到新创建的f-test-branch分支
8. `git branch -d f-test-branch` -- 删除分支
9. `git merge --no-ff master` -- 向前合并分支到主干
10. git分支管理

	- 主分支 
	- 主开发分支   
	- 临时性分支   
		
		- 功能(feature)分支
		- 预发布(release)分支
		- 修补BUG(fixbug)分支
		
11. `git tag -a 0.1.1` -- 创建tag
12. `git reset --hard HEAD ` -- revert
13. `git reset --hard ORIG_HEAD ` -- revert the commit files
14. `git fetch origin` -- fetch from server
15. `git reset --hard origin/master` --


####5. OS X下git status中文会显示为编码的解决方案

    git config --global core.quotepath false

###五、mysql

      1. desc tablename; -- 查看表结构
      2. show databases; -- 查看所有的数据
      3. show tables; -- 查看表


