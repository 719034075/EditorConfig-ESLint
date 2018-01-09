# 什么是EditorConfig

`EditorConfig`帮助开发人员在不同的编辑器和IDE之间定义和维护一致的编码风格。
`EditorConfig`项目由两部分组成。
1. `.editorconfig`文件（format）。这个文件统一定义编码的具体风格。
2. 对应的文本编辑器的`editorconfig`插件。

这些插件使开发者能够了解并遵守统一定义的编码样式、风格。
`.editorconfig`文件易于阅读，并且与版本控制系统很好地协作。

# EditorConfig文件是什么模样的

下面是一个用`.editorconfig`文件定义`Python`和`JavaScript`文件的行尾和缩进样式的的例子。

```.editorconfig
# EditorConfig is awesome: http://EditorConfig.org

# top-most EditorConfig file
# 最顶级的editorconfig文件，意味着editorconfig插件从子目录的editorconfig文件搜索到此文件就会停止搜索。
root = true

# Unix-style newlines with a newline ending every file
# Unix风格的文末换行符，匹配所有的文件
[*]
end_of_line = lf
insert_final_newline = true

# Matches multiple files with brace expansion notation
# 用括号拓展符号匹配多个类型的文件
# Set default charset
# 设置默认的编码类型（UTF-8）
[*.{js,py}]
charset = utf-8

# 4 space indentation
# 设置*.py的缩进类型为space--4个空格
[*.py]
indent_style = space
indent_size = 4

# Tab indentation (no size specified)
[Makefile]
indent_style = tab

# Indentation override for all JS under lib directory
[lib/**.js]
indent_style = space
indent_size = 2

# Matches the exact files either package.json or .travis.yml
[{package.json,.travis.yml}]
indent_style = space
indent_size = 2
```

[更多真实环境中的样例，可供查询。](https://github.com/editorconfig/editorconfig/wiki/Projects-Using-EditorConfig)

# 这些文件存放在项目的哪里

当打开一个文件时,`.editorconfig`插件会在打开的文件的目录和每个父目录中查找名为`.editorconfig`的文件。
如果到达根文件路径或找到`root = true`的`.editorconfig`文件，则将停止搜索`.editorconfig`文件。
所以说，整个项目可以有多个`.editorconfig`文件分布在各级目录中。但是最终都会搜索到一个根`.editorconfig`文件。

`.editorconfig`文件是从外到内读取的。
最近的`.editorconfig`文件是最后读取的。
要求的样式风格属性按照它们被读取的顺序被应用。
因此在更接近的文件中的属性优先。