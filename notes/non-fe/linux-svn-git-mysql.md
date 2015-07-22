##linux\svn\git\mysql等常用命令使用记录

[svn命令详解](http://blog.csdn.net/wklken/article/details/6594956)    
[vi命令详解](http://www.cnblogs.com/88999660/articles/1581524.html)     
[git命令详解](http://blog.csdn.net/ithomer/article/details/7529022)     
[源码安装nginx](http://www.nginx.cn/install)    



###一、svn命令
    
      1. svn co svn://10.10.10.60/xiaoju/server/trunk/api/v2/views
      2. svn export svn://10.10.10.60/xiaoju/server/trunk/api/v2/views 一般用于打包程序，不会包含.svn文件夹
      3. svn ci  filename -m "checkin note”
      4. svn st -v/-u
      5. svn up
      6. svn up –r 200 file.c 将本地的file.c还原为200版本，并提交到服务器【本地是拿下来了，版本库端并没有被变】
      7. svn diff filename
      8. svn diff  -r 12302:12304 home.html
      9. svn diff get_hb_list.tpl |vim -R -
      10. svn diff filename -r1234:2345[|vim -R -]
      11. svn log filename
      12. svn delete filename
      13. svn delete –force over-there －－强制删除
      14. svn add filename －－增加文件到本地svn数据库
      15. svn propset svn:ignore "*.jpg"
      16. svn list svn://10.10.10.60/xiaoju/server/trunk/api/v2/views －－查看svn在某个目录下纳入管理的文件列表
      17. svn import $DIR $URL -m “Something your want to mark.” －－将本地目录纳入svn版本管理
      18. svn mkdir－－svn mkdir newdir，－－svn mkdir -m "Making a new dir." http://svn.red-bean.com/repos/newdir
      19. svn cat -r 10528 home.html －－查看历史版本
      20. svn resolve --accept working compressed，svn revert compressed－－解决目录compressed树冲突
      21. ci的时候出现 xx.html is out of date－－解决方法就是先update一下，然后再ci
      22. svn revert filename
      22. 冲突的解决方法：
        1. 先将.mine文件拷贝到你自己的文件
        2. 先跟test.html跟低版本的比较
        3. 再将test.html跟高版本的比较
        4. 解决完冲突之后再diff一下
        5. 然后设置svn resolved test.html
        6. 然后ci
        
  


###二、Linux命令（实用篇）

    
      1. scp  -r  $DIR $DIR －－scp -r 113.11.197.199:~/app/api/v2/views/webapp/home.html . 12505cp -r 
      2. tar xvf filename.tar－－解包（tar是打包不是压缩）
      3. tar cvf filename.tar DIRNAME－－打包
      4. gunzip gilename.gz－－解压gz文件
      5. gzip -d filename.gz－－解压文件
      6. gzip filename－－压缩为filename.gz
      7. tar zxvf filename.tar.gz－－解压.tar.gz并解包
      8. tar zcvf filename.tar.gz DIRNAME－－打包文件夹并压缩为tar.gz


###三、Linux命令（不常用篇）

      1. hostname－－显示主机名
      2. top－－显示进程
      3. tail -f /home/xiaoju/php/logs/v2/didi.log.wf  |grep wxtransaction -A10 —color
      4. tail -f access.log |grep 'p_login'
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
      9. curl ifconfig.me
    

###四、mysql

      1. desc tablename;
      2. show databases;
      3. show tables;


###五、git命令

####Create a new repository on the command line

    touch README.md
    git init
    git add README.md
    git commit -m "first commit"
    git remote add origin git@github.com:liujb/c-study.git
    git push -u origin master
    
####Push an existing repository from the command line

    git remote add origin git@github.com:liujb/c-study.git
    git push -u origin master
    
###OS X下git status中文会显示为编码的解决方案

    git config --global core.quotepath false