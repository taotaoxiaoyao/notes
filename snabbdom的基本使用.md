## 常用的Virtual DOM库
- [Snabbdom](https://github.com/snabbdom/snabbdom)
  - Vue 2.x 内部使用的 Virtual DOM 就是改造的 Snabbdom
  - 大约 200 SLOC（single line of code）
  - 通过模块可扩展
  - 源码使用 TypeScript 开发
  - 最快的 Virtual DOM 之一
- [virtual-dom](https://github.com/Matt-Esch/virtual-dom)

## 学习Snabbdom前的准备
1. 创建项目，并安装parcel
```js
// 创建项目目录
mkdir snabbdom
// 进入目录
cd snabbdom
// 创建package.json
yarn init -y
// 本地安装 parcel
yarn add parcel-bundler -D
```
2. 创建项目结构

  ```txt
  │  index.html
  │  package.json
  └─src
     │  index.js
  ```
3. 配置package.json中的scripts字段

  ```json
  {
    "name": "snabbdom",
    "version": "1.0.0",
    "main": "./src/index.js",
    "license": "MIT",
    "scripts": {
        "dev": "parcel index.html --open",
        "build": "parcel build index.html"
    },
    "devDependencies": {
        "parcel-bundler": "^1.12.5"
    }
  }

```
  4. 安装[Snabbdom](https://github.com/snabbdom/snabbdom)
  ```bash
  yarn add snabbdom@2.1.0
  ```
  5. [可选]克隆2.1.0版本代码到本地
  ```bash
  git clone -b v2.1.0 --depth=1 https://github.com/snabbdom/snabbdom.git
  ```
  6. 导入Snabbdom 

- Snabbdom 的两个核心函数 init 和 h() 
  - init() 是一个高阶函数，返回patch() 
  - h() 返回虚拟节点VNode

```js
import { init } from 'snabbdom/init'
import { h } from 'snabbdom/h'
console.log('init, h: ', init, h);
// 控制台运行
npm run dev
```
报以下错误：
```js
Cannot resolve dependency 'snabbdom/init.js'
```
原因分析：
1. 在node_modules下的snabbdom模块的build/package/文件夹下有init.js和h.js，而不是snabbdom/int/目录下；
2. snabbdom/int/路径是在package.json中的exports字段设置的，parcel和webpack4及其以下版本不支持exports这个字段。该字段的作用是在导入snabbdom/init的时候会根据映射补全路径成snabbdom/build/package/init.js。
```json
// exports字段
"exports": {
    "./init": "./build/package/init.js",
    "./h": "./build/package/h.js",
    "./helpers/attachto": "./build/package/helpers/attachto.js",
    "./hooks": "./build/package/hooks.js",
    "./htmldomapi": "./build/package/htmldomapi.js",
    "./is": "./build/package/is.js",
    "./jsx": "./build/package/jsx.js",
    "./modules/attributes": "./build/package/modules/attributes.js",
    "./modules/class": "./build/package/modules/class.js",
    "./modules/dataset": "./build/package/modules/dataset.js",
    "./modules/eventlisteners": "./build/package/modules/eventlisteners.js",
    "./modules/hero": "./build/package/modules/hero.js",
    "./modules/module": "./build/package/modules/module.js",
    "./modules/props": "./build/package/modules/props.js",
    "./modules/style": "./build/package/modules/style.js",
    "./thunk": "./build/package/thunk.js",
    "./tovnode": "./build/package/tovnode.js",
    "./vnode": "./build/package/vnode.js"
  }
```
解决方法：
补全路径引入模块
```js
import { init } from "snabbdom/build/package/init.js";
import { h } from "snabbdom/build/package/h.js";
console.log('init, h: ', init, h);
```