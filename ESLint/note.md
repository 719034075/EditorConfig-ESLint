# 什么是ESLint

`ESLint`是一个根据`ECMAScript`标准以及按照配置文件的规则对`JavaScript`代码进行**检测**并**给出报告**的工具。

在日常开发中，`ESLint`被用来避免低级错误和统一代码风格。

`ESLint`被设计为完全可配置的。主要有两种方式来配置`ESLint`

+   在注释中配置。使用JavaScript注释直接把配置嵌入到JS文件中。
+   配置文件。使用下面任一的文件来为全部的目录和它的子目录指定配置信息。

    * JavaScript：`.eslintrc.js`
    * YAML：`.eslintrc.yaml`或者`eslintrc.yml`
    * JSON：`.eslintrc.json`
    * 废弃的用法？：`.eslintrc`
    * package.json：`package.json`中创建`eslintConfig`属性

这些文件的优先级则是按照以上出现的顺序（`.eslintrc.js` > `.eslintrc.yaml` > `.eslintrc.yml` > `.eslintrc.json` > `.eslintrc` > `package.json`）。

# 开始

## 安装和使用

+ 安装要求：Node.js(>=4.x),npm 2+
+ 安装方式：本地和全局

### 本地安装

如果你想要将eslint作为项目构建系统的一部分，那么建议使用本地安装。

```cmd
npm install eslint --save-dev
```

然后创建一个配置文件。

```cmd
./node_modules/.bin/eslint --init

//创建的过程中会问你一系列的问题，根据自己的需求回答，会给选项。
? How would you like to configure ESLint?
? Are you using ECMAScript 6 features?
? Are you using ES6 modules?
? Where will your code run？
? Do you use JSX?
? Do you use React?
? What style of indentation do you use?
? What quotes do you use for strings?
? What line endings do you use?
? Do you require semicolons?
? What format do you want your config file to be in?
```
完成上面的问答之后会在项目的根目录中生成一个`.eslintrc.js`文件

最后在你的项目根目录运行`ESLint`。
```cmd
./node_modules/.bin/eslint .eslintrc.js
```

### 全局安装

对应局部安装的过程分别是
```cmd
npm install -g eslint
```

```cmd
eslint --init
```

```cmd
eslint yourfile.js
```

## 文件配置方式

这里只提及一部分关于js格式的配置。
[详尽内容参见官网](https://eslint.org/docs/user-guide/configuring)

`env`：你的脚本运行的环境。不同的环境中的全局变量不尽相同。

```
//运行在浏览器和node中
// .eslintrc.js
module.exports = {
  env: {
    browser: true,
    node: true,
  },
};
```

 [所有的环境值查看官网](https://eslint.org/docs/user-guide/configuring#specifying-environments)

`globals`：额外的全局变量。

```
// .eslintrc.js
module.exports = {
  globals: {
    vue: true,
    wx: true,
  },
};
```

`parserOptions`：语言选项

```
"parserOptions": {
   // ECMAScript 版本
  "ecmaVersion":6,
  "sourceType":"script",//module
  // 想使用的额外的语言特性:
  "ecmaFeatures":  {
  // 允许在全局作用域下使用 return 语句
  "globalReturn":true,
  // impliedStric
  "impliedStrict":true,
  // 启用 JSX
  "jsx":true
   }
 },
```

`rules.md`:开启规则和发生错误时报告的等级

+ `off`或`0`：关闭规则
+ `warn`或`1`：打开规则，作为警告
+ `error`或`2`：打开规则，作为错误

```
module.exports = {
  rules: {
    eqeqeq: 'off',
    curly: 'error',
  },
};
```

可以配合webpack、gulp等工具使用。

# 在webstorm中的使用

1. `ctrl+alt+s`打开设置。
2. `Languages&Frameworks>JavaScript>Code Quality Tools>ESLint`开启`ESLint`。
3. 配置相应路径即可。

# ESLint的三种常见规范
[Airbnb](https://github.com/airbnb/javascript)

[Google](https://github.com/google/eslint-config-google)

[Standard](https://github.com/standard/standard)