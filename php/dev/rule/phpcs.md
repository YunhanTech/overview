# phpcs

## 安装
```
composer global require "squizlabs/php_codesniffer=*"
```

## 配置（PHPSTORM）
```
## 获取phpmd安装路径
composer global config bin-dir --absolute


## 配置md路径
File -> Default Setting -> Languages & Frameworks -> PHP
    -> Code Sniffer -> ... -> 添加phpcs路径 -> Apply

## 设置规则
File -> Default Setting -> Editor -> Inspections -> PHP
     -> PHP Code Sniffer validation （打上勾）-> Coding standard -> PSR2 -> Apply
```
