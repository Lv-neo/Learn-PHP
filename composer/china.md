# composer优化，安装类库

##中国全量镜像

```
composer config -g repo.packagist composer https://packagist.phpcomposer.com
```

##composer token

进入https://github.com/settings/tokens 点击 「Generate new token」 新建一个 Token，选择默认新建就行，然后就会得到一个 Token，然后输入这个值就 OK 了。

##Q&A

```
Your requirements could not be resolved to an installable set of packages
```

执行
```
composer global require "fxp/composer-asset-plugin:@dev"
```


