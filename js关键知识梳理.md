## JavaScript关键知识梳理
### JavaScript运行：基础语法规则、编译与执行阶段、运行环境
### 模块化：为什么需要模块化、模块化规范
### 运行堆栈：数据类型、高阶函数、闭包
### 面向对象编程：构造函数与new关键字、this指向、原型及原型链

####  
  new的过程 :
    1、创建一个空对象
    2、给这个对象添加一个原型
    3、将函数中的this 指向当前对象
    4、执行函数代码（堆栈执行逻辑）
    5、返回这个对象的内存地址
    函数体内有return，如果是引用类型，返回引用类型，如果是基本数据类型，返回原本对象的内存地址。

  this :
    1、this 永远指向一个对象
    2、this 的指向完全取决于运行环境（对象）
    3、正常状态：this指向当前的运行环境，（哪个对象调用， this 就执行哪个对象）
    4、构造函数 this 指向 new 时创建的空对象
    5、箭头函数中是没有this的，因此，this指向上一个原型。
    6、模拟new一个对象
    ```
      //ctor函数名字 ，params函数参数
      function _new( ctor, ...params) {
        // 1、创建一个空对象
        // let obj = {}
        // 2、赋值原型
        // obj.__proto__ = Ctor.prototype
        // 1 + 2 创建一个空对象 + 赋值原型
        let obj = Object.create(Ctor.prototype)
        // 3、改变this 指向 指向空对象
        // 4、执行函数代码
        let ret = Ctor.call(obj, ...params)
        // 5、返回对象地址
        if (ret !== undefind && /^(object|function)$.test/(typeof ret)) return ret;
        return obj;
      }
    ```
    7、实例对象的获取原型的方法： __proto__, Object.getPrototypeOf(实例对象)
### 异步编程： 执行线程、EventLoop、Promise、Async/Await

