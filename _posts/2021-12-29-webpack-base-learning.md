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
* style-loader 将样式通过<style/>标签插入到head中
* 配置loader时，loader是链式调用，执行顺序是从右到左的，所以如下配置是先执行css-loader 
![image.png](https://s2.loli.net/2021/12/30/EmoZ5YqHSzAItKB.png)

### 解析图片和字体
 * file-loader 用于处理文件， png/svg/jpg/gif 等；
 * file-loader 也可用于处理字体文件，woff/woff2/eot/ttf/otf 等
 * url-loader 也可以处理图片和字体，可以设置较小资源自动base64
 ![image.png](https://s2.loli.net/2022/01/04/wAYBIkQMTW2rbqL.png)
 
 ### webpack中的文件监听
 * 文件监听是在发现源码发生变化时，自动重新构建出新的输出文件
 * webpack 开启监听模式，有两种方式：
 
   启动webpack 命令时，带上 --watch 参数
   在配置 webpack.config.js 中设置 watch:true
 * 文件监听的原理分析
   轮询判断文件的最后编辑时间是否变化
   某个文件发生了变化。并不会立刻告诉监听者，而是县缓存起来，等aggregateTimeout
 ![image.png](https://s2.loli.net/2022/01/04/MdNwtJlg7sX6Z15.png)
  
 ### webpack 中的热更新及原理分析
 * 热更新 webpack-dev-server, wds不刷新浏览器，wds不输出文件而是放在内存中，使用HotModuleReplacementPlugin插件
 * 热更新 webpack-dev-middleware, wdm将webpack输出的文件传输给服务器，适用于灵活场景的定制
 * 热更新原理分析：
 ![image.png](https://s2.loli.net/2022/01/04/RnrfWpB5xezw3s2.png)
 
 ### 文件指纹策略：chunkhash、contentHash和hash
 * Hash: 和整个项目的构建相关，只要项目文件有修改，整个项目构建的hash值就会更改
 * Chunkhash: 和webpack打包的chunk有关，不同的entry会生成不同的chunkhash值
 * Contenthash: 根据文件内容来定义hash，文件内容不变则contenthash不变
 * 设置output的filename，使用[chunkhash]
 
 ### HTML、CSS和JavaScript代码压缩
 * JS文件压缩，内置了 uglifyjs-webpack-plugin
 * Css文件压缩，使用optimize-css-assets-webpack-plugin（webpack5使用css-minimizer-webpack-plugin） 同时使用cssnano
 * Html文件压缩，修改html-webpack-plugin，设置压缩参数
 

> 有三个比较容易混淆的概念，bundle，chunk和module。
bundle：打包最终生成的文件
chunk：每个chunk是由多个module组成，可以通过代码分割成多个chunk。
module：webpack中的模块（js、css、图片等等）
 
 
 
 
 
 
 
 

