# php7新特性 yaconf

Yaconf是一种容器配置,它解析ini文件,并当PHP是开启时将结果存储在PHP。

[github地址](https://github.com/laruence/yaconf)

##安装
在Linux中编译Yaconf

* Yaconf是一个PECL扩展，简单安装

```
$ pecl install yaconf
```
* 或者你可以自己编译

http://pecl.php.net/package/yaconf
```
$ /path/to/php7/bin/phpize
$ ./configure --with-php-config=/path/to/php7/bin/php-config
$ make && make install
```

##运行时配置

*	yaconf.directory

```
   path to directory which all ini configuration files are placed in
```

* yaconf.check_delay

```
   in which interval Yaconf will detect ini file's change(by directory's mtime),
   if it is set to zero, you have to restart php to reloading configurations.
```

##Api

```
mixed Yaconf::get(string $name, mixed $default = NULL)

bool Yaconf::has(string $name)

```

##示例

###配置文件目录
在php.ini里我们设置配置文件目录
```
yaconf.directory=/tmp/yaconf
```

###INI配置文件
在/tmp/yaconf中设置2个配置文件

foo.ini
```
name="yaconf"
year=2015
features[]="fast"
features.1="light"
features.plus="zero-copy"
features.constant=PHP_VERSION
features.env=${HOME}
```

bar.ini
```
[base]
parent="yaconf"
children="NULL"

[children:base]
children="set"
```

###运行
```
php7 -r 'var_dump(Yaconf::get("foo"));'
/*
array(3) {
  ["name"]=>
  string(6) "yaconf"
  ["year"]=>
  string(4) "2015"
  ["features"]=>
  array(5) {
    [0]=>
    string(4) "fast"
    [1]=>
    string(5) "light"
    ["plus"]=>
    string(9) "zero-copy"
    ["constant"]=>
    string(9) "7.0.0-dev"
    ["env"] =>
    string(16) "/home/huixinchen"
  }
}
*/

```


