# composer

* [Composer Packagist 中国全量镜像](http://www.phpcomposer.com/)

* [Composer 中文网](http://docs.phpcomposer.com/)

* [packageist](https://packagist.org/)


##依赖管理
Composer 不是一个包管理器。是的，它涉及 "packages" 和 "libraries"，但它在每个项目的基础上进行管理，在你项目的某个目录中（例如 vendor）进行安装。默认情况下它不会在全局安装任何东西。因此，这仅仅是一个依赖管理。
这种想法并不新鲜，Composer 受到了 node's npm 和 ruby's bundler 的强烈启发。而当时 PHP 下并没有类似的工具。
Composer 将这样为你解决问题：
a) 你有一个项目依赖于若干个库。
b) 其中一些库依赖于其他库。
c) 你声明你所依赖的东西。
d) Composer 会找出哪个版本的包需要安装，并安装它们（将它们下载到你的项目中）。

##声明依赖关系
比方说，你正在创建一个项目，你需要一个库来做日志记录。你决定使用 monolog。为了将它添加到你的项目中，你所需要做的就是创建一个 ```composer.json``` 文件，其中描述了项目的依赖关系。

```
{
    "require": {
        "monolog/monolog": "1.2.*"
    }
}
```

##系统要求
运行 Composer 需要 PHP 5.3.2+ 以上版本。一些敏感的 PHP 设置和编译标志也是必须的，但对于任何不兼容项安装程序都会抛出警告。
我们将从包的来源直接安装，而不是简单的下载 zip 文件，你需要 git 、 svn 或者 hg ，这取决于你载入的包所使用的版本管理系统。
Composer 是多平台的，我们努力使它在 Windows 、 Linux 以及 OSX 平台上运行的同样出色。

##全局安装

```
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
```



