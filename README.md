
## 介绍
    本组件用于进行文件替换的简单基础框架

## 使用方式

````PHP
    $replacements = [
        '/{{namespacePath}}/' => 'Admin',
        '/{{RNT}}/'           => 'Task',
    ];

    $replacementsCallback = [];

    // 读取模板
    $reader = new TemplateFileReader(__DIR__ . '/templates/ReplaceName.tpl');
    // 实例化引擎
    $engine = new TemplateEngine($reader);
    // 初始化配置
    $engine->setContentReplacements($replacements)->setContentReplacementsCallback($replacementsCallback);
    // 执行替换
    $engine->replaceContentReplacements()->replaceContentReplacementsCallback();
    // 写入文件
    $writer = new TemplateFileWriter(__DIR__ . '/templates/Admin.php');
    // 写入操作
    $result = $writer->setContent($engine->getReplaceResult())->setForce(true)->saveFile();
    // 或: $writer->setContent($engine->getReplaceResult())->saveFile();
    var_dump($result);
````
