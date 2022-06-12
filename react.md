### react知识点笔记记录

1、如果setState在React 能够控制的范围内，它就是异步的，如果不在，就是同步的。例如，setTimeout, 浏览器开启异步线程，没有react。

2、setState会进行状态合并，合并以后只进行一次rerender,函数也是一样的。合并是避免频繁的rerender。

3、setState执行过程：会将需要修改的动作先存在队列里面，等所有setState都添加完成以后，再进行执行队列里面的更改，全部执行完成后，执行render

  setState-》将状态临时存储到组件中更新器中 -》 判断是否为批量更新模式-》 是，则将组件更新器存储到更新队列中， setState方法所处的函数执行完成后开始进行批量更新操作- 从更新队列中找到更新器并执行。不是的话，则 更新组件 --》 计算组件状态 -》 虚拟DOM对比 -》 将差异更新到DOM中

4、如果想在setTimeout里不让每次setState都render一次如下
   import { unstable_batchedUpdates } from 'react-dom'
    在setTimeout里利用unstable_batchedUpdates把需要执行的函数传进去。之后会把这个函数传递给react。