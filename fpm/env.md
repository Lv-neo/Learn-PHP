# php注册加载环境变量

[toc]

##php7 使用yaconf加载环境变量
[yaconf](../ya/yaconf.md)

##php5 传统加载环境变量方式

###设置一个脚本导入环境变量
```
$ vim /sh/env.sh
$ export MYSQL_A_HOST='127.0.0.1'
$ export MYSQL_A_PORT=3306
$ export MYSQL_A_PASSWORD='test'
$ export MYSQL_A_USERNAME='xxxxxx'
```

###在启动脚本/etc/init.d/php-fpm中加载脚本
```
#! /bin/sh

### BEGIN INIT INFO
# Provides:          php-fpm
# Required-Start:    $remote_fs $network
# Required-Stop:     $remote_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: starts php-fpm
# Description:       starts the PHP FastCGI Process Manager daemon
### END INIT INFO

prefix=/usr/local/php
exec_prefix=${prefix}

php_fpm_BIN=${exec_prefix}/sbin/php-fpm
php_fpm_CONF=${prefix}/etc/php-fpm.conf
php_fpm_PID=${prefix}/var/run/php-fpm.pid

#加载环境脚本
source /sh/env.sh
......
```

###将系统环境变量注入到php环境变量
```
$ vim php-fpm.conf

env[MYSQL_A_HOST]=$MYSQL_A_HOST
env[MYSQL_A_PORT]=$MYSQL_A_PORT
env[MYSQL_A_PASSWORD]=$MYSQL_A_PASSWORD
env[MYSQL_A_USERNAME]=$MYSQL_A_USERNAME
```

###重启系统，检查环境变量
```
$ service php-fpm restart
$ php -r "var_dump(getenv('MYSQL_A_HOST'));"  
$ 127.0.0.1
```

