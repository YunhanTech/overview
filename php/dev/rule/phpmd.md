# phpmd

## 规则
- 下载此项目
- 文件：/overview/php/dev/rule/phpmd/ruleset.xml

## 安装
```
composer global require "phpmd/phpmd"
```

## 配置（PHPSTORM）
```
## 获取phpmd安装路径
composer global config bin-dir --absolute


## 配置md路径
File -> Default Setting -> Languages & Frameworks -> PHP
    -> Mess Detector -> ... -> 添加phpmd路径 -> Apply

## 设置规则
File -> Default Setting -> Editor -> Inspections -> PHP
    -> PHP Mess Detector validation （打上勾）-> 添加额外规则（见上面规则说明） -> Apply
```
