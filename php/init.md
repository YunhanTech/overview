# 环境初始化

## Composer 安装
#### 全局安装
````
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer

# 设置全局path
# 打印路径：composer global config bin-dir --absolute
vim ~/.bash_profile
export PATH=${PATH}:~/.composer/vendor/bin/

# 设置国内镜像
composer config -g repo.packagist composer https://packagist.phpcomposer.com
````

## IDE - PHPStorm
- [下载安装](https://www.jetbrains.com/phpstorm/)
- [破解](http://idea.lanyus.com/)
- PHP_CS, PHP_MD
    - 安装
        ````
        composer global require "squizlabs/php_codesniffer=*"
        composer global require "phpmd/phpmd"
        ````
    - PhpStorm 配置
        ````
        File -> Default Setting -> Languages & Frameworks -> PHP
            -> Code Sniffer -> ... -> 添加phpcs路径 -> Apply
            -> Mess Detector -> ... -> 添加phpmd路径 -> Apply
        
        File -> Default Setting -> Editor -> Inspections -> PHP
            -> PHP Code Sniffer validation （打上勾）-> Coding standard -> PSR2 -> Apply
            -> PHP Mess Detector validation （打上勾）-> Options（选择所有规则) -> Apply
        ````