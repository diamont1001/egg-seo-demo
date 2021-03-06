# egg-ssr-demo

基于 `node egg` 框架的服务器渲染前端 web 项目原型，前端代码使用 `webpack` 进行编译，前端模块使用 `ejs` 模块语言进行渲染，当然模块语言可以根据自己的喜好来进行替换。

| 功能 | 框架 |
| -- | -- |
| 基础框架 | [egg](http://eggjs.org) |
| 前端代码编译打包 | webpack 4.x |
| 前端模板 | [ejs](http://ejs.co/#install)（不喜欢的可以替换，很方便） |


## npm scripts

- 安装依赖：`yarn install`
- 开发调试：开两个窗口，一个编译前端代码 `npm run devFe`，另外一个运行服务器代码 `npm run dev`，浏览器打开 [http://localhost:7001/](http://localhost:7001/)
- 发布前编译：`npm test && npm run build`
- 运行：`npm start`
- 停止：`npm stop`


## 重要目录

```
-- app [服务端代码]
    -- controller [路由控制器]
    -- view [ejs 模板，包含前端代码]
        -- modules [模块]
        -- pages [页面，每个页面建立一个，如：'detail']
    -- config [配置文件]
-- logs [日志]
```

注意：`ejs` 模块里引用的模块，在 `js` 里记得把对应模块的 `js` 也引入进来。比如 `pages/home.js` 里就需要 `require('../../modules/header)`。

## 缓存更新

每次开发完新功能后，一些静态资源（JS/CSS）都有可能会有更新的，为了让线上能马上更新到最新的静态资源，每次发布前，可以修改以下的配置项对静态资源进行更新。

> config/config.default.js

```js
config.layoutVersion = '2018081501';
```

## 参考文档
- [egg](http://eggjs.org)
- [ejs](http://ejs.co/#install)
