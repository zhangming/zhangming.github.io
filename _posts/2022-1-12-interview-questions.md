![image.png](https://s2.loli.net/2022/01/12/VGTFUqfWowJnxMr.png)
参考文章：<https://juejin.cn/post/6844904116339261447>

## JavaScript 基础
![image.png](https://s2.loli.net/2022/01/12/vWb7eZc8PmMXszT.png)

* 1.介绍下JavaScript的执行上下文      
    简而言之，执行上下文是评估和执行 JavaScript 代码的环境的抽象概念。每当 Javascript 代码在运行的时候，它都是在执行上下文中运行。   
    JavaScript 的可执行代码(executable code)的类型：全局代码、函数代码、eval代码。      
    JavaScript 引擎创建了执行上下文栈（Execution context stack，ECS）来管理执行上下文。 
    创建执行上下文会发生三件事情：1.this值的决定，即我们所熟知的this绑定；2.创建词法环境组件；3.创建变量环境组件。
    
  
* 2.介绍下JavaScript的作用域
