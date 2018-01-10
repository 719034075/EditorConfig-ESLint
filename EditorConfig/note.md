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

> Tips: Windows下只要创建一个名为`.editorconfig.`的文件，Windows会自动转成`.editorconfig`。否则会要求你必须键入文件名。

# 常用属性详解

`indent_style`\
缩进样式\
属性值不区分大小写，会被核心库统一成小写。\
可选值:
+ `tab`
+ `space`

支持所有插件。

`indent_size`\
缩进大小\
属性值不区分大小写，会被核心库统一成小写。\
可选值:
+ 一个整数（常用为`2`或`4`）
+ `tab`


如果`indent_size`的值为`tab`,那么`indent_size`的具体大小会是`tab_width`指定的一个tab的大小，否则是编辑器本身的一个`tab`大小。

支持所有插件。

`tab_width`\
一个`tab`的大小\
可选值:
+ 一个正整数（当`index_size`是个数字时，则默认为`index_size`）

支持所有插件。

`end_of_line`\
换行符格式\
属性值不区分大小写，会被核心库统一成小写。\
可选值:
+ `lf`（Unix格式，只用换行。`\n`，一般用这个）
+ `crlf`（Windows格式，回车换行。`\r\n`）
+ `cr`（Mac格式，只用回车。`\r`）

支持所有插件。

`charset`\
字符编码\
属性值不区分大小写，会被核心库统一成小写。\
可选值:
+ `latin1`
+ `utf-8`（一般用这个）
+ `utf-16be`
+ `utf-16le`

支持所有插件。

`trim_trailing_whitespace`\
行尾是否允许空格\
属性值不区分大小写，会被核心库统一成小写。\
可选值:
+ `true`
+ `false`

支持所有插件。

`insert_final_newline`\
文件夹末尾是否以空行结束\
属性值不区分大小写，会被核心库统一成小写。\
可选值:
+ `true`
+ `false`

支持所有插件。

[更多属性](https://github.com/editorconfig/editorconfig/wiki/EditorConfig-Properties)

常用`.editorconfig`文件
```editorcongif
# http://editorconfig.org

root = true

# 对所有文件生效
[*]
charset = utf-8
indent_style = space
indent_size = 2
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true

# 对后缀名为 md 的文件生效
[*.md]
trim_trailing_whitespace = false

```

# 在webstorm中的使用

1. `ctrl+alt+s`打开设置。
2. `editor>code style`下面有一个`Enable EditorConfig support`选中前面的复选框，启动支持。
3. 后面有个`export`按钮是用来导出当前IDE的`.editorconfig`配置文件。

之后就可以根据自己的需求来配置`.editorconfig`配置文件。
`ctrl+alt+L`格式当前文件。
