# php-fpm介绍
PHP-FPM(FastCGI Process Manager：FastCGI进程管理器)对于PHP 5.3.3之前的php来说，是一个补丁包，旨在将FastCGI进程管理整合进PHP包中。如果你使用的是PHP5.3.3之前的PHP的话，就必须将它patch到你的PHP源代码中，在编译安装PHP后才可以使用。

从PHP 5.4 RC2开始，php-fpm已经转正了，不再被php团队标注为EXPERIMENTAL（实验性的东西）。

相对Spawn-FCGI，PHP-FPM在CPU和内存方面的控制都更胜一筹，而且前者很容易崩溃，必须用crontab进行监控，而PHP-FPM则没有这种烦恼。

PHP5.3.3已经集成php-fpm了，不再是第三方的包了。PHP-FPM提供了更好的PHP进程管理方式，可以有效控制内存和进程、可以平滑重载PHP配置，比spawn-fcgi具有更多优点，所以被PHP官方收录了。在./configure的时候带 –enable-fpm参数即可开启PHP-FPM。

###使用PHP-FPM来控制PHP-CGI的FastCGI进程

```
/usr/local/php/sbin/php-fpm{start|stop|quit|restart|reload|logrotate}
--start 启动php的fastcgi进程
--stop 强制终止php的fastcgi进程
--quit 平滑终止php的fastcgi进程
--restart 重启php的fastcgi进程
--reload 重新平滑加载php的php.ini
--logrotate 重新启用log文件
```

