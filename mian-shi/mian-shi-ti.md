# 面试题

## 浏览器

### fetch与XMLHttpRequest

#### fetch的缺点：

* 浏览器支持不好
* 默认无cookie
* 错误不会被拒绝
* 不支持超时
* 终止fetch
* 不支持progress

## React

### 渲染原理

#### 节点类型

* DOM节点
* 文本节点
* 空节点
* 数组节点
* 组件节点：函数组件和类组件

![](../.gitbook/assets/image%20%287%29.png)

#### 对比更新

* key值的作用用于通过旧节点找到对应的新节点，key值应该在一定范围内唯一\(兄弟节点中\)并保持稳定

## 工程化

### webpack

#### 原理

1. 初始化参数：从配置文件和 Shell 语句中读取与合并参数，得出最终的参数；
2. 开始编译：用上一步得到的参数初始化 Compiler 对象，加载所有配置的插件，执行对象的 run 方法开始执行编译；
3. 确定入口：根据配置中的 entry 找出所有的入口文件；
4. 编译模块：从入口文件出发，调用所有配置的 Loader 对模块进行翻译，再找出该模块依赖的模块，再递归本步骤直到所有入口依赖的文件都经过了本步骤的处理；
5. 完成模块编译：在经过第4步使用 Loader 翻译完所有模块后，得到了每个模块被翻译后的最终内容以及它们之间的依赖关系；
6. 输出资源：根据入口和模块之间的依赖关系，组装成一个个包含多个模块的 Chunk，再把每个 Chunk 转换成一个单独的文件加入到输出列表，这步是可以修改输出内容的最后机会；
7. 输出完成：在确定好输出内容后，根据配置确定输出的路径和文件名，把文件内容写入到文件系统。

## 性能优化

### 传输

#### 资源加载时序

defer、async、url combo、资源位置

#### ssr

#### 缓存

端内缓存

模块缓存

#### 资源大小

* 压缩
* tree-shaking
* code-splitting



### 渲染

#### virtual dom

#### 图片懒加载：

intersection observer



## http

### http2.0与http1.1的区别

1、性能提升：http2.0采用二进制分帧层传输数据而不是http1.1的文本格式

2、多路复用：上面提到HTTP/1.1的线头阻塞和多个TCP连接的问题，HTTP2的多路复用完美解决。HTTP2让所有的通信都在一个TCP连接上完成，真正实现了请求的并发

3、头部压缩

4、服务器端推送

## CSS

### BFC

## JS

#### 原型

![](../.gitbook/assets/image%20%288%29.png)

### 事件循环

#### 宏任务

setTimeout、setInterval、I/O、UI渲染、setImmeDiate、requestAnimationFrame

#### 微任务

Promise、MutationObserver、Process.nextTick



