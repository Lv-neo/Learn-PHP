# 'zend_mm_heap corrupted' Error

>最近小伙伴反馈给我，项目站点偶尔白屏，我检查了日志后发现php-fpm的error.log中出现很多WARNING: [pool www] child 21673 said into stderr: "zend_mm_heap corrupted"的错误，并导致子进程退出

查询资料后，简而言之就是zend内存管理崩溃

解决方案有几种种

* 增大output_buffering （增加到4096后，过几天又出现了）
* 关闭output_buffering  (并不想关闭output_buffering)
* 命令行执行export USE_ZEND_ALLOC=0 （这个环境变量处理）
* 修改opcache.enable_cli=0 


###网上还有一种说法
表示php extension有bug，排除法检查php extension

https://serverpilot.io/community/articles/fix-php-error-zend_mm_heap-corrupted.html





