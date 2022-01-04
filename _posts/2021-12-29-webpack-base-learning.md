### 为什么需要构建工具
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
* 入口文件，单页面的值是个string，多页面值是Object里面是key value 格式指定入口
![image.png](https://s2.loli.net/2021/12/29/PX6kSKnYma85jgR.png)

### webpack 核心概念之output
* output 用来告诉webpack 如何将编译后的文件输出到磁盘
* 单入口output 配置
 ![image.png](https://s2.loli.net/2021/12/29/Jo9qM8TPelxZ4vH.png)
* 多入口output 配置
![image.png](https://s2.loli.net/2021/12/29/oaQD6n3rVLychBm.png)

### webpack 核心概念之loaders
* webpack原生只支持JS和JSON两种文件类型
* 通过loaders去支持其它文件类型，把它们转换成有效的模块，并且可以添加到依赖图中
* 本身是个函数，接受源文件作为参数，返回转换的结果
* 常用的loaders
![image.png](https://s2.loli.net/2021/12/29/HK9XNCkTFBa3rSz.png)
* loaders的用法
![image.png](https://s2.loli.net/2021/12/29/UISWo31AEkxvdBn.png)
![image.png](https://s2.loli.net/2021/12/29/Mk8URN976Yayoqn.png)

### webpack 核心概念之plugins
* 用于bundle文件的优化，资源管理和环境变量注入，作用于整个构建过程
* 常见的Plugins
![image.png](https://s2.loli.net/2021/12/29/usYcrFXBhIQZngR.png)
* Plugins的用法
![image.png](https://s2.loli.net/2021/12/29/ptd6SFglvCaHLrQ.png)

### webpack 核心概念之mode
* Mode用来指定当前的构建环境是：production、development、还是 none
* 设置Mode可以使用webpack内置的函数，默认值为production
* Mode的内置函数功能
![image.png](https://s2.loli.net/2021/12/29/M5vduhjI6SKYzRy.png)
* Mode的使用方法  mode:"production"

### 解析ECMAScript6和React JSX
* 安装 babel-loader: npm i @babel/core @babel/preset-env babel-loader -D
* 增加 .babelrc文件
![image.png](https://s2.loli.net/2021/12/30/OHb9Ty2er3EDWFw.png)

### 解析Css、Less和Sass
* css-loader 用于加载.css文件，并且转化成commonjs对象、
* style-loader 将样式通过<style>标签插入到head中
* 配置loader时，loader是链式调用，执行顺序是从右到左的，所以如下配置是先执行css-loader
 
![image.png](https://s2.loli.net/2021/12/30/EmoZ5YqHSzAItKB.png)

 
### 解析图片和字体
 
 
 
 

