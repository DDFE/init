###nginx配置

	 location /api 
     {
         rewrite ^/api/(.*?)/(.*)$ /api/$1/index.php/$2 break;
         fastcgi_index index.php;
         fastcgi_pass 127.0.0.1:9000;
         include fastcgi.conf;                                                                                 
     }
  
###ci框架

1. 需要在nginx配置的root目录 `/home/xiaoju/developers`放入`/api/v2/index.php`。
2. index.php中需修改system路径为`$system_path = '/home/xiaoju/app/system';` 注意是在app中的system
3. index.php中修改application folder为 `$application_folder = '/home/xiaoju/app/api/v2';`注意是app中的api

###nginx
1. 日志：tail -f access.log |grep 'p_login' --color
2. reload：
	
	1. cd nginx
	2. sudo ./sbin/nginx -s reload
	