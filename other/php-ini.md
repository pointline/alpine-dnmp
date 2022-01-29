# php 修改配置

## php.ini
```ini
max_execution_time = 18000
memory_limit = 2G
error_reporting = E_ALL
display_errors = On
display_startup_errors = On
; track_errors = On 废弃

# opcache
opcache.enable=1
opcache.enable_cli=1
opcache.memory_consumption=128
opcache.interned_strings_buffer=8
opcache.save_comments=1
```

## php-fpm.d下的www.conf文件

```ini
user = www-data
group = www-data

; listen = 127.0.0.1:9000
listen = 9000
```