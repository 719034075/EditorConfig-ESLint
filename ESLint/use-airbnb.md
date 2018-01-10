# 使用Airbnb规范

1. 在项目中初始化一个package.json
```cmd
npm init
```

2. 全局安装

```cmd
npm install -g eslint eslint-plugin-react eslint-plugin-import eslint-plugin-jsx-a11y eslint-config-airbnb eslint-config-airbnb-base
```

3. 本地安装

```cmd
npm install --save-dev eslint eslint-plugin-react eslint-plugin-import eslint-plugin-jsx-a11y eslint-config-airbnb eslint-config-airbnb-base
```

4. 项目中初始化`.eslintrc`文件

```cmd
eslint --init
```

```
//选第二个
? How would you like to configure ESLint? (Use arrow keys)
  Answer questions about your style
> Use a popular style guide
  Inspect your JavaScript file(s)

//选第二个
? Which style guide do you want to follow? (Use arrow keys)
  Google
> Airbnb
  Standard

//有没有使用React，没有就选N
? Do you use React? (y/N)

//保存格式,我用JSON
? What format do you want your config file to be in? (Use arrow keys)
  JavaScript
  YAML
> JSON
```

5. 在webstorm中配置

`Ctrl+alt+S`打开设置。
`Languages&Frameworks->JavaScript->Code Quality Tools->ESLint`
把`Enable`复选框勾中即可。