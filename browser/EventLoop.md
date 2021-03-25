## EventLoop

#### 什么是 EventLoop

EventLoop 是指一套事件循环并发模型，因为 JavaScript 是一个单线程脚本语言，所以执行事件运行脚本的顺序就会变得很重要，而事件循环(EventLoop)，就是负责执行代码、收集和处理事件以及执行队列，中每次轮回执行顺序的模型。
由于输入输出和执行体不一样，这使到浏览器下的 EventLoop 和 Node 的 EventLoop 不一样，虽然他们都是基于 V8 引擎。

#### 浏览器的 EventLoop



宏任务(macrotasks):

宏任务包括事件： `setTimeout`、`setInterval`、`setImmediate`、`requestAnimationFrame`、`I/O`、UI rendering


微任务(microtasks):
微任务包括事件： `Promises.then`、`Promise.catch`、`Promise.finally`、`queueMicroTask`、`MutationObserver`




## 参考连接

[什么是 Event Loop？——阮一峰](https://www.ruanyifeng.com/blog/2013/10/event_loop.html)

[深入解析你不知道的 EventLoop 和浏览器渲染、帧动画、空闲回调（动图演示）](https://juejin.cn/post/6844904165462769678)

[浏览器的 Event Loop](https://mp.weixin.qq.com/s/8ldkuaoZHqAiofJtPi6nzA)