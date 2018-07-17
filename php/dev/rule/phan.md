# Phan
## 简介
Phan是一个PHP的静态分析器，它倾向于最小化误报。它试图证明错误而不是正确。

它会查找常见问题，并在类型信息可用或可以推断时验证各种操作的类型兼容性。

## 扩展安装
- ast
    - [windows](https://windows.php.net/downloads/pecl/releases/ast/0.1.6/)
    - mac: `pecl install ast`
- pcntl.so
    - mac: 用源码编译安装
    - windows: 不支持

## 入门
```
## 安装
composer require --dev phan/phan

## 初始化配置
vendor/bin/phan --init --init-level=3

## 执行
vendor/bin/phan

## 执行(windows)
sh vendor\bin\phan
```

## 核心配置解读 .phan/config.php
````php
return [
    // 开启的子进程数量，需要使用pcntl扩展，windows不支持，mac安装后，可以修改
    'processes' => 1,
    
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

## [忽略部分报错](https://github.com/phan/phan/wiki/Annotating-Your-Source-Code)：建议尽量不要使用
### `suppress` 忽略整个方法
````
class D {
    /**
     * @suppress PhanUndeclaredClassMethod
     */
    function g() {
        C::f();
    }
}
````

### `@phan-suppress-current-line` 忽略当前行
```
function test_line_suppression() {
    echo $undef1;  // @phan-suppress-current-line PhanUndeclaredVariable
    echo $undef2 + missingFn();
}
```

### `@phan-suppress-next-line` 忽略下一行
````
function test_line_suppression() {
    // @phan-suppress-next-line PhanUndeclaredVariable, PhanUndeclaredFunction
    echo $undefVar2 + missing_function();  
}
````
