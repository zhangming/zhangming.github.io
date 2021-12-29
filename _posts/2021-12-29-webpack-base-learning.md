### 为设什么需要构建工具
* 转换ES6语法
* 转换JSX
* css前缀补全/预处理器
* 压缩混淆
* 图片压缩

### 前端构建演变之路
* ant + YUI TOOL -> grunt ->fis3/gulp -> rollup/webpack/parcel

### 初识webpack
* webpack 默认配置文件：webpack.config.js
* 可以通过webpack --config 指定配置文件
![image.png](https://s2.loli.net/2021/12/29/sfdgIBkKSGWelnv.png)

### 环境搭建：安装webpack
* 安装 nvm
* 安装Node.js 和 NPM

### webpack 初体验：一个最简单的例子
* mkdir my-project
* npm init -y
* npm install webpack webpack-cli --save-dev
* 配置entry,output 完成最简单的打包
![image.png](https://s2.loli.net/2021/12/29/xOLjdPibGHneRva.png)


### 通过npm script 运行webpack
* package.json 增加script 命令
![image.png](https://s2.loli.net/2021/12/29/XjpEr15ovCKbGL9.png)

### webpack 核心概念之entry
* 入口文件，单页面的值是个string,多页面值是Object里面是key value 格式指定入口
![image.png](https://s2.loli.net/2021/12/29/PX6kSKnYma85jgR.png)
