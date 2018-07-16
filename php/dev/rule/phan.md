# Phan
## 简介
Phan是一个PHP的静态分析器，它倾向于最小化误报。它试图证明错误而不是正确。

它会查找常见问题，并在类型信息可用或可以推断时验证各种操作的类型兼容性。

## 入门
```
## 安装
composer require --dev phan/phan

## 初始化配置
vendor/bin/phan --init --init-level=3

## 执行
vendor/bin/phan

## 执行(windows)
php vendor/bin/phan
```

## 核心配置解读 .phan/config.php
````php
return [
    // 执行时使用cpu核数
    'processes' => 4,
    
    // 开启进度条
    'progress_bar' => true,
    
    // 解析的目录（包含依赖，依赖需要从exclude剔除）
    'directory_list' => [
        'app',
        'vendor' // 建议最小化原则，少加载文件
    ],
    
    // 不需要解析的目录
    'exclude_analysis_directory_list' => [
        'vendor',
        '.phan',
    ],
    
    // 需要解析的单独的文件
    'file_list' => [],
    
    // 需要剔除的文件列表
    'exclude_file_list' => [],
    
    // 自动加载的内部类库，一般用于加载扩展stub，下面引入了laravel的stub
    'autoload_internal_extension_signatures' => [
        'laravelIdeHelper' => '_ide_helper.php',
        'laravelMeta' => '.phpstorm.meta.php'
    ],
]
````
