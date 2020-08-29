# 项目描述
# 自动生成 vue routes 到 @/routes/temp.router.js

待最终完善!

根据 @/src/pages/**/meta.json 自动生成 vue routes

> 执行时机： webpack.base.config.js 中自执行

```js
// in webpack.base.config.js
...
require('./makeRoutes')
...

```

特点:
1. 自动递归识别生成目录层级，支持无限级
2. 结合导航组件自动生成菜单，支持无限级
3. 各路径权限单独配置，无需写成一个大文件
3. 修改页面路径直接修改文件夹名称即可
4. 自动对路径转中划线处理
5. 采用`meta.json`方式配置页面元信息实现更多定制化需求场景
6. 监听 `src/pages` 目录下的 `meta.json` 文件变化自动重新创建路由

示例: meta.json
```js
{ 
    "menu": {//如果不需要展示主界面菜单上，则不配置 menu 项
      "title": "看板管理",
      "icon": "el-icon-s-help"
    },
    "hideInBread": true,
    "access": [
      "ADMIN",
      "USER VISITOR",
      "GUEST",
      "VISITOR"
    ] 
}
```

注意事项：
1. 在根目录下 **.gitignore** 文件追加一行忽略匹配规则 `temp.*`
2. 在根目录下 **.eslintignore** 文件追加一行忽略匹配规则 `temp.*`