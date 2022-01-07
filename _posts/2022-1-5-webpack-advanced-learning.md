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
   >eval:使用eval包裹模块代码
    source map: 产生.map文件
    cheap: 不包含列信息
    inline: 将.map作为DataURI嵌入，不单独生成.map文件
    module:包含loader的sourcemap
    
### 提取页面公共资源
* 





