## webpack 进阶

### 自动清理构建目录产物
* 通过npm scripts 清理构建目录 rm -rf ./dist && webpack 或者 rimraf ./dist && webpack
* 避免构建前每次都要手动删除dist，使用 clean-webpack-plugin(默认会删除output指定的输出目录)

### PostCSS插件autoprefixer自动补齐css3前缀
* 具体配置如下：
![image.png](https://s2.loli.net/2022/01/05/Je1MnxKur4hLQYw.png)

### 移动端CSS PX自动转换成rem
* 移动端机型众多，分辨率不同，需要做适配
* 最早的适配，CSS 媒体查询实现响应式布局，缺陷：要写多套适配样式代码
* css3 推出rem的适配单位，w3c对rem定义：font-size of the root element
* rem和px的对比：rem 是相对单位，px 是绝对单位
* 使用 px2rem-loader将px转换成rem，页面渲染时计算根元素的font-size值


### 静态资源内联
* 资源内联的意义：
  代码层面：页面框架初始化脚本，上报相关打点，css内联避免页面闪动
  请求层面：减少HTTP网络请求（小图片或者字体内联 url-loader）
* 内联html和js：raw-loader
![image.png](https://s2.loli.net/2022/01/05/YrhUOTaAzk6XWl1.png)
* css内联 ：style-loader 或 html-inline-css-webpack-plugin


### 多页面应用打包通用方案
* 多页面打包的基本思路：每个页面对应一个entry,一个html-webpack-plugin(缺点：每次新增或删除页面需要改webpack配置)
* 多页面打包通用方案：动态获取entry和设置html-webpack-plugin数量，利用glob.sync
    `entry: glob.sync(path.join(__dirname,'./src/*/index.js'))`


### 使用 sourcemap
* 作用：通过source map 定位到源代码
* 开发环境开启，线上环境关闭（线上排查问题的时候可以将sourcemap上传到错误监控系统）
* source map 关键字：   
    eval:使用eval包裹模块代码     
    source map: 产生.map文件     
    cheap: 不包含列信息    
    inline: 将.map作为DataURI嵌入，不单独生成.map文件    
    module:包含loader的sourcemap    
    
### 提取页面公共资源
* 基础库分离：将 react、react-dom基础库通过cdn引入，不打入bundle中
* 使用html-webpack-externals-plugin
* 利用SplitChunksPlugin进行公共脚本分离（webpack4内置的，替代CommonsChunkPlugin插件，chunks参数说明：async 异步引入的库进行分离，initial 同步引入的库进行分离，all 所有引入的库进行分离）
![image.png](https://s2.loli.net/2022/01/07/AYo1bcOj6zuVga8.png)

### Tree Shaking的使用和原理分析
* 摇树优化，概念:1 个模块可能有多个⽅方法，只要其中的某个⽅方法使⽤用到了了，则整个⽂文件都会被打到 bundle ⾥里里⾯面去，tree shaking 就是只把⽤用到的⽅方法打⼊入 bundle ，没⽤用到的⽅方法会在 uglify 阶段被擦除掉
* 使用:webpack 默认⽀支持，在 .babelrc ⾥里里设置 modules: false 即可。 production mode的情况下默认开启
* 要求:必须是 ES6 的语法，CJS 的⽅方式不不⽀支持

* DCE（Elimination）代码不不会被执行，不可到达;代码执行的结果不会被用到;代码只会影响死变量(只写不不读)
* Tree-shaking原理：
  >利⽤ ES6 模块的特点:    
  只能作为模块顶层的语句句出现    
  import 的模块名只能是字符串串常量量   
  import binding 是 immutable的    
  代码擦除: uglify 阶段删除⽆无⽤用代码   


### Scope Hoisting使用和原理分析
* 现象:构建后的代码存在⼤量闭包代码


