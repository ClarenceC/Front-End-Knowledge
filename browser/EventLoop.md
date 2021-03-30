## EventLoop

#### 什么是 EventLoop

EventLoop 是指一套事件循环并发模型，因为 JavaScript 是一个单线程脚本语言，所以执行事件的顺序就会变得很重要，而事件循环(EventLoop)，就是负责执行代码、收集和处理事件以及执行队列中每次轮回执行顺序的原理模型。
由于输入输出和执行体不一样，这使到浏览器下的 EventLoop 和 Node 的 EventLoop 不一样，虽然他们都是基于 V8 引擎。

#### 浏览器的 EventLoop

宏任务(macrotasks):

宏任务包括事件： `setTimeout`、`setInterval`、`setImmediate`、`requestAnimationFrame`、`I/O`、`Network`


微任务(microtasks):
微任务包括事件： `Promises.then`、`Promise.catch`、`Promise.finally`、`queueMicroTask`、`MutationObserver`


![images](./images/eventLoop.png)
浏览器在 1 帧(1Frame)里, 运行 Event Loop 和 渲染流程

基于[深入解析你不知道的 EventLoop 和浏览器渲染、帧动画、空闲回调（动图演示）](https://juejin.cn/post/6844904165462769678)整理

## 参考连接

[JavaScript 运行机制详解：再谈Event Loop__阮一峰](http://www.ruanyifeng.com/blog/2014/10/event-loop.html)

[深入解析你不知道的 EventLoop 和浏览器渲染、帧动画、空闲回调（动图演示）](https://juejin.cn/post/6844904165462769678)

[浏览器的 Event Loop](https://mp.weixin.qq.com/s/8ldkuaoZHqAiofJtPi6nzA)

[事件循环：微任务和宏任务](https://zh.javascript.info/event-loop)

[微任务、宏任务与Event-Loop](https://juejin.cn/post/6844903657264136200)