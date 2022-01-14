![image.png](https://s2.loli.net/2022/01/12/VGTFUqfWowJnxMr.png)
参考文章：<https://juejin.cn/post/6844904116339261447>

## JavaScript 基础
![image.png](https://s2.loli.net/2022/01/12/vWb7eZc8PmMXszT.png)

* 1.介绍下JavaScript的执行上下文      
    简而言之，执行上下文是评估和执行 JavaScript 代码的环境的抽象概念。每当 Javascript 代码在运行的时候，它都是在执行上下文中运行。   
    JavaScript 的可执行代码(executable code)的类型：全局代码、函数代码、eval代码。      
    JavaScript 引擎创建了执行上下文栈（Execution context stack，ECS）来管理执行上下文。 
    创建执行上下文会发生三件事情：1.this值的决定，即我们所熟知的this绑定；2.创建词法环境组件；3.创建变量环境组件。
    > function test(num){
        var a = "2";
        return a+num;
    }
    test(1);
    
    * 执行流开始 初始化function test，test函数会维护一个私有属性 [[scope]],并使用当前环境的作用域链初始化，在这里就是 test.[[Scope]]=global scope.     
    * test函数执行，这时候会为test函数创建一个执行环境，然后通过复制函数的[[Scope]]属性构建起test函数的作用域链。此时 test.scopeChain = [test.[[Scope]]]   
    * test函数的活动对象被初始化，随后活动对象被当做变量对象用于初始化。即 test.variableObject = test.activationObject.contact[num,a] = [arguments].contact[num,a]    
    * test函数的变量对象被压入其作用域链，此时 test.scopeChain = [ test.variableObject, test.[[scope]]];     
    至此test的作用域链构建完成

    
  
* 2.介绍下JavaScript的作用域
