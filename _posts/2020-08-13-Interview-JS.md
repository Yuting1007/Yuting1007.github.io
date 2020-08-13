---
layout: post
title: "Interview-JS"
date: 2020-08-13
tag: Interview
---
### BOM
[Notes](https://github.com/huyaocode/webKnowledge/blob/master/JS%E5%9F%BA%E7%A1%80/BOM.md)

browser object model (浏览器模型， 主要处理浏览器窗口和框架， 描述了与**浏览器进行交互的方法和接口**， 可以对浏览器窗口进行访问和操作)
* BOM && DOM
BOM 的 window 包含了 document， 因此通过 window 对象的 document 属性就可以访问、 检索、 修改文档内容与结构。**document 对象又是 DOM 模型的根节点**。
因此， BOM 包含了 DOM， 浏览器提供出来给予访问的是 BOM 对象， **从 BOM 对象再访 问到 DOM 对象**， 从而 js 可以操作浏览器以及浏览器读取到的文档
* BOM 对象包含的内容
Window; Navigator 客户端浏览器的信息； History 浏览器窗口访问过的url; Location 当前url 的信息； Screen 客户端显示屏的信息
* 检测浏览器版本版本有哪些方式？
	 -   根据 navigator.userAgent // UA.toLowerCase().indexOf('chrome')
	-   根据 window 对象的成员 // 'ActiveXObject' in window
* offsetWidth/offsetHeight,clientWidth/clientHeight 与 scrollWidth/scrollHeight 的区别

	-   offsetWidth/offsetHeight 返回值包含 content + padding + border，效果与 e.getBoundingClientRect()相同
	-   clientWidth/clientHeight 返回值只包含 content + padding，如果有滚动条，也不包含滚动条
	-   scrollWidth/scrollHeight 返回值包含 content + padding + 溢出内容的尺寸

### DOM
[Notes](https://github.com/huyaocode/webKnowledge/blob/master/JS%E5%9F%BA%E7%A1%80/DOM.md)
[Video Note](https://www.youtube.com/watch?v=YIG2_UB-C7o&list=PL4cUxeGkcC9gfoKa5la9dsdCNpuey2s-V&index=6)

* **文档对象模型 (DOM) 是HTML和XML文档的编程接口**。它提供了对文档的结构化的表述，并定义了一种方式可以使从程序中对该结构进行访问，从而改变文档的结构，样式和内容。DOM 将文档解析为一个由节点和对象（包含属性和方法的对象）组成的结构集合。简言之，它会将web页面和脚本或程序语言连接起来

* DOM 标准采用捕获+冒泡。两种事件流都会触发 DOM 的所有对象，从 window 对象开始，也在 window 对象结束。
* Event 常见应用， `event.target, event.currentTarget, event.preventDefault(), event.stopPropagation(), event.stopImmediatePropagation()`
* 事件委托 
事件委托是指将事件绑定目标元素的到父元素上，利用冒泡机制触发该事件
* 自定义事件
```
var evt = new Event("myEvent");

someDom.addEventListener("myEvent", function () {
  //处理这个自定义事件
});

someDom.dispatchEvent(evt);
```
* JS 获取dom 的CSS的方式
`currentStyle[attr]`
```
function getStyle(obj, attr) {
  if (obj.currentStyle) {
    return obj.currentStyle[attr];
  } else {
    return window.getComputedStyle(obj, false)[attr];
  }
}
```
* DOM 操作
	* 创建新节点

		-   createDocumentFragment() //创建一个 DOM 片段
		-   createElement() //创建一个具体的元素
		-   createTextNode() //创建一个文本节点

	* 添加、移除、替换、插入

		-   appendChild()
		-   removeChild()
		-   replaceChild()
		-   insertBefore() //在已有的子节点前插入一个新的子节点

	* 查找

		-   getElementsByTagName() //通过标签名称
		-   getElementsByName() // 通过元素的 Name 属性的值(IE 容错能力较强，会得到一个数组，其中包括 id 等于 name 值的)
		-   getElementById() //通过元素 Id，唯一性
* Window VS document
Document 对象是 Window 对象的一部分，即 window.document. 
**Window对象表示当前浏览器的窗口**， 是JS的顶级对象， 创建的所有对象函数变量都是window的成员； **Document 对象是 HTML 文档的根节点与所有其他节点**（元素节点，文本节点，属性节点, 注释节点， 可以通过document在脚本对HTML 页面的所有元素进行访问。

### ES6
[Notes](https://github.com/huyaocode/webKnowledge/blob/master/JS%E5%9F%BA%E7%A1%80/ES6.md)
* var, let, const 区别
	* 全局申明的 var 变量会挂载在 window 上，而 let 和 const 不会
	* var 声明变量存在变量提升，let 和 const 不会
	* let、const 的作用范围是块级作用域，而 var 的作用范围是函数作用域
	* 同一作用域下 let 和 const 不能声明同名变量，而 var 可以
	* 同一作用域下在 let 和 const 声明前使用会存在暂时性死区
	* const
		- 一旦声明必须赋值,不能使用 null 占位
		- 声明后不能再修改
		- 如果声明的是复合类型数据，可以修改其属性
* map 
作用是生成一个新数组，遍历原数组，将每个元素拿出来做一些变换然后返回一个新数组，原数组不发生改变
All value are truthy excepty for : false, 0, ""(empty string), null, undefined and NaN
```
var arr = [1, 2, 3];
var arr2 = arr.map((item) => item + 1);
arr; //[ 1, 2, 3 ]
arr2; // [ 2, 3, 4 ]
```
```
['1', '2', '3'].map(parseInt);
// -> [ 1, NaN, NaN]
```
map((value, index, arr) =>{} )
parseInt(value, radix) 多的话会被忽略
[Explaination](https://medium.com/dailyjs/parseint-mystery-7c4368ef7b21)
* filter
[Some application examples](https://juejin.im/post/6844903890387746830)
 filter 的作用也是生成一个新数组，在遍历数组的时候将返回值为 true 的元素放入新数组，我们可以利用这个函数删除一些不需要的元素
 arr.filter((element, index, arr) => {})
 应用有： 过滤，删掉"", undefined, null, 去重
```
let arr = [1, 2, 2, 3, 4, 5, 5, 6];
let newArr = arr.filter((x, index,self)=>self.indexOf(x)===index) 
console.log(newArr); //[1, 2, 3, 4, 5, 6]
```
* Reduce
reduce 可以将数组中的元素通过回调函数最终转换为一个值。 如果我们想实现一个功能将函数里的元素全部相加得到一个值，可能会这样写代码
对于 reduce 来说，它接受两个参数，分别是回调函数和初始值
比如说求和
```
const arr = [1,2,3]
const sum = arr.reduce((acc, curr)=>{acc + curr}, 0)
```
回调函数接受四个参数，分别为累计值、当前元素、当前索引、原数组，后三者想必大家都可以明白作用，这里着重分析第一个参数

* ES6 arrow function VS normal function
	* 普通 function 的声明在变量提升中是最高的，箭头函数没有函数提升
	* 箭头函数没有属于自己的this，arguments
	* 箭头函数不能作为构造函数，不能被 new，没有 property
	* 不可以使用 yield 命令，因此箭头函数不能用作 Generator 函数
	* 不可以使用 new 命令，因为：
		- 没有自己的 this，无法调用 call，apply
		- 没有 prototype 属性 ，而 new 命令在执行时需要将构造函数的 prototype 赋值给新的对象的 __proto__

*  Promise
	* promise chain
Promise 实现了链式调用，也就是说每次调用 then 之后返回的都是一个 Promise，并且是一个全新的 Promise，原因也是因为状态不可变。如果你在 then 中 使用了 return，那么 return 的值会被 Promise.resolve() 包装。
```
Promise.resolve(1)
  .then((res) => {
    console.log(res); // => 1
    return 2; // 包装成 Promise.resolve(2)
  })
  .then((res) => {
    console.log(res); // => 2
  });
```
* async && await
async 就是将函数返回值使用 Promise.resolve() 包裹了下，和 then 中处理返回值一样，并且 await 只能配套 async 使用.
[await perfect example](https://github.com/huyaocode/webKnowledge/blob/master/JS%E5%9F%BA%E7%A1%80/ES6.md)

* generator
首先 Generator 函数调用和普通函数不同，它会返回一个迭代器
```
function* generatorExample(){}
const generator = generatorExample();
```
有next()这个method. 
```
function* foo(x) {
  let y = 2 * (yield x + 1);
  let z = yield y / 3;
  return x + y + z;
}
let it = foo(5);
console.log(it.next()); // => {value: 6, done: false}
console.log(it.next(12)); // => {value: 8, done: false}
console.log(it.next(13)); // => {value: 42, done: true}
```
-   首先 Generator 函数调用和普通函数不同，它会返回一个迭代器
   
	-   当执行第一次 next 时，传参会被忽略，并且函数暂停在 yield (x + 1) 处，所以返回 5 + 1 = 6
	    
	-   当执行第二次 next 时，**传入的参数等于上一个 yield 的返回值**，如果你不传参，yield 永远返回 undefined。此时 let y = 2 _ 12，所以第二个 yield 等于 2 _ 12 / 3 = 8
	    
	-   当执行第三次 next 时，传入的参数会传递给 z，所以 z = 13, x = 5, y = 24，相加等于 42
* 原理
当 yeild 产生一个值后，生成器的执行上下文就会从栈中弹出。但由于迭代器一直保持着队执行上下文的引用，上下文不会丢失，不会像普通函数一样执行完后上下文就被销毁
* 私有方法和私有属性
私有方法和私有属性，是只能在类的内部访问的方法和属性，外部不能访问.

	- **将私有方法移出类，放到模块里**
	- 还有一种方法是利用**Symbol 值的唯一性**，将私有方法的名字命名为一个 Symbol 值

* Proxy
Proxy 可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写。
ES6 原生提供 Proxy 构造函数，用来生成 **Proxy 实例**。
```
var proxy = new Proxy(target, handler)
```
Proxy 对象的所有用法，都是上面这种形式，不同的只是`handler`参数的写法。其中，`new Proxy()`表示生成一个`Proxy`实例，`target`参数表示所要拦截的目标对象，`handler`参数也是一个对象，用来定制拦截行为。
一个技巧是将 Proxy 对象，设置到`object.proxy`属性，从而可以在`object`对象上调用。
```javascript
var object = { proxy: new Proxy(target, handler) };
```
`proxy`对象是`obj`对象的原型，`obj`对象本身并没有`time`属性，所以根据原型链，会在`proxy`对象上读取该属性，导致被拦截。
```javascript
var proxy = new Proxy({}, {
  get: function(target, propKey) {
    return 35;
  }
});

let obj = Object.create(proxy);
obj.time // 35
```
同一个拦截器函数，可以设置拦截多个操作。
```javascript
var handler = {
  get: function(target, name) {
    if (name === 'prototype') {
      return Object.prototype;
    }
    return 'Hello, ' + name;
  },

  apply: function(target, thisBinding, args) {
    return args[0];
  },

  construct: function(target, args) {
    return {value: args[1]};
  }
};

var fproxy = new Proxy(function(x, y) {
  return x + y;
}, handler);

fproxy(1, 2) // 1
new fproxy(1, 2) // {value: 2}
fproxy.prototype === Object.prototype // true
fproxy.foo === "Hello, foo" // true

```
### 原型链和继承
#### 原型
-   JavaScript 的**所有对象**中都包含了一个  `__proto__`  内部属性，这个属性所对应的就是该对象的原型
-   JavaScript 的**函数对象**，除了原型  `__proto__`  之外，还预置了 prototype 属性
- 当函数对象作为构造函数创建实例时，该 prototype 属性值将被作为实例对象的原型 `__proto__`
![enter image description here](https://lh3.googleusercontent.com/v3G4RBq5qI6m8Bsk7NqFv8GpvIJzI3frHUy9W4PUsxZOV5v7DWuwvBk_Fl7GdreId9P2QPVIptQ)
#### 原型链
任何一个实例对象通过原型链可以找到它对应的原型对象，原型对象上面的实例和方法都是实例所共享的。

一个对象在查找以一个方法或属性时，他会先在自己的对象上去找，找不到时，他会沿着原型链依次向上查找。
#### instanceOf原理
判断实例对象的**proto**属性与构造函数的 prototype 是不是用一个引用。如果不是，他会沿着对象的**proto**向上查找的，直到顶端 Object。
#### 判断对象是哪个类
`object.constructor`
#### new的时候发生了什么
```
var object = {}
object.__proto__ = Base.prototype
Base.call(object)
```
1.  创建一个新的对象 obj;
2.  将这个空对象的**proto**成员指向了 Base 函数对象 prototype 成员对象
3.  Base 函数对象的 this 指针替换成 obj, 相当于执行了 Base.call(obj);
4.  如果构造函数显示的返回一个对象，那么则这个实例为这个返回的对象。 否则返回这个新创建的对象
```
function _new(func, ...args) {
  let obj = Object.create(func.prototype); // 原型
  let res = func.apply(obj, args); // 初始化对象属性
  return res instanceof Object ? res : obj; // 返回值
}
```
#### class
```
//ES6
class Animal(){
	constructor(){
		this.name = "name";
	}
}
//normal
function Animal(){
	this.name = "name"
}
```
consrtuctor本质上就是一个构造函数
#### 继承
* 构造函数法
原理： 将子类的 this 使用父类的构造函数跑一遍
缺点： Parent 原型链上的属性和方法并不会被子类继承
```
function Parent() {
  this.name = "parent";
}

function Child() {
  Parent.call(this);
  this.type = "child";
}
```
* 原型链实现继承
原理：把**子类的 prototype（原型对象    **直接设置为父类的实例
缺点：因为子类只进行一次原型更改，所以子类的所有实例保存的是同一个父类的值。 当子类对象上进行值修改时，如果是修改的原始类型的值，那么会在实例上新建这样一个值； 但如果是引用类型的话，他就会去修改子类上唯一一个父类实例里面的这个引用类型，这会影响所有子类实例
```
function Parent() {
  this.name = "parent";
  this.arr = [1, 2, 3];
}

function Child() {
  this.type = "child";
}

Child.prototype = new Parent();
var c1 = new Child();
var c2 = new Child();
c1.__proto__ === c2.__proto__;
```
组合继承优化 添加中间对象
```
function Parent() {
  this.name = "parent";
  this.arr = [1, 2, 3];
}

function Child() {
  Parent.call(this);
  this.type = "child";
}

Child.prototype = Object.create(Parent.prototype); //提供__proto__
Child.prototype.constrctor = Child;
```
### this
#### this 的指向有哪几种情况
1.  作为函数**直接调用**，非严格模式下，this 指向 **window**，严格模式下，this 指向 undefined；
2.  作为某对象的方法调用，**this 通常指向调用的对象**。
3.  使用 apply、call、bind 可以绑定 this 的指向。
4.  在**构造函数中，this 指向新创建的对象**
5.  箭头函数没有单独的 this 值，t**his 在箭头函数创建时确定**，它与声明所在的上下文相同

-   _this_  alone refers to the global variable, in a browser, it is  `[object Window]`
-   _this_  in function refers to the object called the function.
-   _this_  in event handlers refers to the HTML element that received the event
-   _this_  in arrow function refers to the object that defined it.
-   _this_  in object refers to the object that owns it
#### 多个this规则出现的时候， this最终指向哪里
首先，new 的方式优先级最高，接下来是 bind 这些函数，然后是 obj.foo() 这种调用方式，最后是 foo 这种调用方式，同时，**箭头函数的 this 一旦被绑定，就不会再被任何方式所改变。**

[Video explaination](https://www.youtube.com/watch?v=gvicrj31JOM)
this refers to the object that is executing the current function.
method -> obj
regular function -> global (window)
new这种情况的话， 会有一个新建的object, 然后function(constructor) 里面的this, 会被指向这个新的object
```
const video = {
	title: 'a';
	tags: ['a', 'b', 'c'];
	showTags(){
		this.tags.forEach((tag)=>{
			console.log(this.title, tag);
		}, this);
	}
}
```
callback function是一个regular function this=> window
forEach() 传入第二个para

### 事件机制
#### 事件触发的三个阶段
事件触发有三个阶段：

-   window 往事件触发处传播，遇到注册的捕获事件会触发
-   传播到事件触发处时触发注册的事件
-   从事件触发处往 window 传播，遇到注册的冒泡事件会触发
就是DOM里面的获取和冒泡
![enter image description here](https://lh3.googleusercontent.com/yvU4dMV-iQF3XfIhvDuJMxzQpsQcNUjJRht7_Hrp1huMoA_2MhDaJdr74X9ShjwzZbU0HkA2je0)
#### target && currentTarget
target 是触发事件的某个具体的对象，只会出现在事件机制的目标阶段，即“**谁触发了事件，谁就是 target** ”。 currentTarget **是绑定事件的对象**。

**官方的解释：**
The `**currentTarget**` read-only property of the [`Event`](https://developer.mozilla.org/en-US/docs/Web/API/Event) interface identifies the current target for the event, as the event traverses the DOM. It always refers to the element to which the event handler has been attached, as opposed to [`Event.target`](https://developer.mozilla.org/en-US/docs/Web/API/Event/target), which identifies the element on which the event occurred and which may be its descendant.
#### 取消默认事件
取消默认操作 w3c 的方法是 e.preventDefault()，IE 则是使用 e.returnValue = false;
```
function cancelHandler(event) {
  var event = event || window.event; //用于IE
  if (event.preventDefault) event.preventDefault(); //标准技术
  if (event.returnValue) event.returnValue = false; //IE
  return false; //用于处理使用对象属性注册的处理程序
}
```
### 事件循环
[Notes](https://github.com/huyaocode/webKnowledge/blob/master/%E5%89%8D%E7%AB%AF%E5%9F%BA%E7%A1%80/JS/%E4%BA%8B%E4%BB%B6%E8%BD%AE%E8%AF%A2%E6%9C%BA%E5%88%B6.md)
#### 任务队列
-   JS 分为同步任务和异步任务
-   同步任务都在主线程上执行，形成一个执行栈
-   主线程之外，事件触发线程管理着一个任务队列，只要异步任务有了运行结果，就在任务队列之中放置一个事件。
-   一旦执行栈中的所有同步任务执行完毕（此时 JS 引擎空闲），系统就会读取任务队列，将可运行的异步任务添加到可执行栈中，开始执行。
![enter image description here](https://lh3.googleusercontent.com/djuYXnwyXjEyR1Z_K3j-B7MHhrB4_vkK72KTXPG7FD782WJlWy3u_fRRw-B8SuiNilAa0eZ4yLM)
### 异步任务
setTimeOut, setInterval; DOM; Promise

#### 关于 setTimeOut、setImmediate、process.nextTick()的比较

- setTimeout()

将事件插入到了事件队列，必须等到当前代码（**执行栈）执行完**，**主线程才会去执行它指定的回调函数**。 当主线程时间执行过长，无法保证回调会在事件指定的时间执行。 浏览器端每次 setTimeout 会有 4ms 的延迟，当连续执行多个 setTimeout，有可能会阻塞进程，造成性能问题。

- setImmediate()

**事件插入到事件队列尾部，主线程和事件队列的函数执行完成之后立即执行**。和 setTimeout(fn,0)的效果差不多。 服务端 node 提供的方法。浏览器端最新的 api 也有类似实现:window.setImmediate,但支持的浏览器很少。

- process.nextTick()

插入到事件队列尾部，但在下次事件队列之前会执行。也就是说，**它指定的任务总是发生在所有异步任务之前，当前主线程的末尾**。 大致流程：当前”执行栈”的尾部–>下一次 Event Loop（主线程读取”任务队列”）之前–>触发 process 指定的回调函数。 服务器端 node 提供的办法。用此方法可以用于处于异步延迟的问题。 可以理解为：此次不行，预约下次优先执行。

### [浏览器的 Tasks、microtasks、 queues 和 schedules](https://github.com/sisterAn/blog/issues/21)

### [浏览器内核](https://github.com/huyaocode/webKnowledge/blob/master/JS%E5%9F%BA%E7%A1%80/node%E4%BA%8B%E4%BB%B6%E8%BD%AE%E8%AF%A2.md)
简单来说浏览器内核是通过取得页面内容、整理信息（应用 CSS）、计算和组合最终输出可视化的图像结果，通常也被称为渲染引擎。

浏览器内核是多线程，在内核控制下各线程相互配合以保持同步，一个浏览器通常由以下常驻线程组成：

-   GUI 渲染线程
-   JavaScript 引擎线程
-   定时触发器线程
-   事件触发线程
-   异步 http 请求线程

### [](https://github.com/huyaocode/webKnowledge/blob/master/JS%E5%9F%BA%E7%A1%80/node%E4%BA%8B%E4%BB%B6%E8%BD%AE%E8%AF%A2.md#1gui-%E6%B8%B2%E6%9F%93%E7%BA%BF%E7%A8%8B)1.GUI 渲染线程

-   主要负责页面的渲染，解析 HTML、CSS，构建 DOM 树，布局和绘制等。
-   当界面需要重绘或者由于某种操作引发回流时，将执行该线程。
-   该线程与 JS 引擎线程互斥，当执行 JS 引擎线程时，GUI 渲染会被挂起，当任务队列空闲时，主线程才会去执行 GUI 渲染。

### [](https://github.com/huyaocode/webKnowledge/blob/master/JS%E5%9F%BA%E7%A1%80/node%E4%BA%8B%E4%BB%B6%E8%BD%AE%E8%AF%A2.md#2js-%E5%BC%95%E6%93%8E%E7%BA%BF%E7%A8%8B)2.JS 引擎线程

-   该线程当然是主要负责处理 JavaScript 脚本，执行代码。
-   也是主要负责执行准备好待执行的事件，即定时器计数结束，或者异步请求成功并正确返回时，将依次进入任务队列，等待 JS 引擎线程的执行。
-   当然，该线程与 GUI 渲染线程互斥，当 JS 引擎线程执行 JavaScript 脚本时间过长，将导致页面渲染的阻塞。

### [](https://github.com/huyaocode/webKnowledge/blob/master/JS%E5%9F%BA%E7%A1%80/node%E4%BA%8B%E4%BB%B6%E8%BD%AE%E8%AF%A2.md#3%E5%AE%9A%E6%97%B6%E5%99%A8%E8%A7%A6%E5%8F%91%E7%BA%BF%E7%A8%8B)3.定时器触发线程

-   负责执行异步定时器一类的函数的线程，如： setTimeout，setInterval。
-   主线程依次执行代码时，遇到定时器，会将定时器交给该线程处理，当计数完毕后，事件触发线程会将计数完毕后的事件加入到任务队列的尾部，等待 JS 引擎线程执行。

### [](https://github.com/huyaocode/webKnowledge/blob/master/JS%E5%9F%BA%E7%A1%80/node%E4%BA%8B%E4%BB%B6%E8%BD%AE%E8%AF%A2.md#4%E4%BA%8B%E4%BB%B6%E8%A7%A6%E5%8F%91%E7%BA%BF%E7%A8%8B)4.事件触发线程

-   主要负责将准备好的事件交给 JS 引擎线程执行。

比如 setTimeout 定时器计数结束， ajax 等异步请求成功并触发回调函数，或者用户触发点击事件时，该线程会将整装待发的事件依次加入到任务队列的队尾，等待 JS 引擎线程的执行。

### [](https://github.com/huyaocode/webKnowledge/blob/master/JS%E5%9F%BA%E7%A1%80/node%E4%BA%8B%E4%BB%B6%E8%BD%AE%E8%AF%A2.md#5%E5%BC%82%E6%AD%A5-http-%E8%AF%B7%E6%B1%82%E7%BA%BF%E7%A8%8B)5.异步 http 请求线程

-   负责执行异步请求一类的函数的线程，如： Promise，axios，ajax 等。
-   主线程依次执行代码时，遇到异步请求，会将函数交给该线程处理，当监听到状态码变更，如果有回调函数，事件触发线程会将回调函数加入到任务队列的尾部，等待 JS 引擎线程执行。
#### Promise

我们知道 Promise 中的异步体现在`then`和`catch`中，所以写在 Promise 中的代码是被当做同步任务立即执行的。

#### [](https://github.com/huyaocode/webKnowledge/blob/master/JS%E5%9F%BA%E7%A1%80/%E4%BA%8B%E4%BB%B6%E9%98%9F%E5%88%97.md#async-await)async await

Async/Await 就是一个自执行的 generate 函数。利用 generate 函数的特性把异步的代码写成“同步”的形式。

async 函数返回一个 Promise 对象，当函数执行的时候，一旦遇到 await 就会先返回，等到触发的异步操作完成，再执行函数体内后面的语句。可以理解为，是让出了线程，跳出了 async 函数体。

### 宏任务
(macro)task（又称之为宏任务），可以理解是每次执行栈执行的代码就是一个宏任务（包括每次从事件队列中获取一个事件回调并放到执行栈中执行）。

浏览器为了能够使得 JS 内部(macro)task 与 DOM 任务能够有序的执行，**会在一个(macro)task 执行结束后，在下一个(macro)task 执行开始前，对页面进行重新渲染**，流程如下：

```
(macro)task->渲染->(macro)task->...
```
(macro)task 主要包含：script(整体代码)、setTimeout、setInterval、I/O、UI 交互事件、postMessage、MessageChannel、setImmediate(Node.js 环境)
#### 微任务
microtask（又称为微任务），**可以理解是在当前 task 执行结束后立即执行的任务**。也就是说，在当前 task 任务后，下一个 task 之前，在渲染之前。

所以它的响应速度相比 setTimeout（setTimeout 是 task）会更快，因为无需等渲染。**也就是说，在某一个 macrotask 执行完后，就会将在它执行期间产生的所有 microtask 都执行完毕（在渲染前）**。

microtask 主要包含：Promise.then、MutaionObserver、process.nextTick(Node.js 环境)
#### 运行机制
-   执行一个宏任务（栈中没有就从事件队列中获取）
-   执行过程中如果遇到微任务，就将它添加到微任务的任务队列中
-   宏任务执行完毕后，立即执行当前微任务队列中的所有微任务（依次执行）
-   当前宏任务执行完毕，开始检查渲染，然后 GUI 线程接管渲染
-   渲染完毕后，JS 线程继续接管，开始下一个宏任务（从事件队列中获取）
![enter image description here](https://lh3.googleusercontent.com/4iYfdvy01SF3RxGAmjoHyHaYfevVhWS4oTYDMnHZrmeWxZ8r5XgpxCrZSCkP0XbCYQ-JvcmdA9g)
#### Promise, async
我们知道 Promise 中的**异步体现在`then`和`catch`**中，所以**写在 Promise 中的代码是被当做同步任务立即执行的**。而在 async/await 中，在出现 await 出现之前，其中的代码也是立即执行的。那么出现了 await 时候发生了什么呢？
**实际上 await 是一个让出线程的标志。await 后面的表达式会先执行一遍，将 await 后面的代码加入到 microtask 中，然后就会跳出整个 async 函数来执行后面的代码。**
**所以 await 后面的代码是 microtask**
[Example](https://github.com/huyaocode/webKnowledge/blob/master/%E5%89%8D%E7%AB%AF%E5%9F%BA%E7%A1%80/JS/%E4%BA%8B%E4%BB%B6%E8%BD%AE%E8%AF%A2%E6%9C%BA%E5%88%B6.md)
### 函数
#### JS调用函数的方式

### 变量类型和类型转化
[Notes](https://github.com/huyaocode/webKnowledge/blob/master/JS%E5%9F%BA%E7%A1%80/%E5%8F%98%E9%87%8F%E7%B1%BB%E5%9E%8B%E5%92%8C%E7%B1%BB%E5%9E%8B%E8%BD%AC%E6%8D%A2.md)
#### 判断类型
```
function getType(target) {
  //先处理最特殊的Null
  if (target === null) {
    return "null";
  }
  //判断是不是基础类型
  const typeOfT = typeof target;
  if (typeOfT !== "object") {
    return typeOfT;
  }
  //肯定是引用类型了
  const template = {
    "[object Object]": "object",
    "[object Array]": "array",
    // 一些包装类型
    "[object String]": "object - string",
    "[object Number]": "object - number",
    "[object Boolean]": "object - boolean",
  };
  const typeStr = Object.prototype.toString.call(target);
  return template[typeStr];
}
```
#### 转换基本类型
对象在转换基本类型时，会调用`valueOf`， 需要转成字符类型时调用`toString`。
比较的时候:
- 判断两者类型是否为 string 和 number，是的话就会将字符串转换为 number
- 判断其中一方是否为 boolean，是的话就会把 boolean 转为 number 再进行判断
- 判断其中一方是否为 object 且另一方为 string、number 或者 symbol，是的话就会把 object 转为原始类型再进行判断
- **两边都是对象的话，那么只要不是同一对象的不同引用，都为 false**
bool:
对象只有在 null 与 undefined 时，才会认定为布尔的 false 值，布尔包装对象本身是个对象，对象->布尔 都是 true，所以 new Boolean(false)其实是布尔的 true
#### 判断一个数据是不是array
-   `Array.isArray(obj)`
    -   ECMAScript 5 种的函数，当使用 ie8 的时候就会出现问题。
-   `obj instanceof Array`
    -   当用来检测在不同的 window 或 iframe 里构造的数组时会失败。这是因为每一个 iframe 都有它自己的执行环境，彼此之间并不共享原型链，所以此时的判断一个对象是否为数组就会失败。此时我们有一个更好的方式去判断一个对象是否为数组。
-   `Object.prototype.toString.call(obj) == '[object Array]'`
    -   这个方法比较靠谱
-   `obj.constructor === Array`
    -   constructor 属性返回对创建此对象的函数的引用

#### Javascript 垃圾回收方法

标记清除（mark and sweep）

-   这是 JavaScript 最常见的垃圾回收方式，当变量进入执行环境的时候，比如函数中声明一个变量，垃圾回收器将其标记为“进入环境”，当变量离开环境的时候（函数执行结束）将其标记为“离开环境”
-   垃圾回收器会在运行的时候给存储在内存中的所有变量加上标记，然后去掉环境中的变量以及被环境中变量所引用的变量（闭包），在这些完成之后仍存在标记的就是要删除的变量了

引用计数(reference counting)

-   在低版本 IE 中经常会出现内存泄露，很多时候就是因为其采用引用计数方式进行垃圾回收。引用计数的策略是跟踪记录每个值被使用的次数，当声明了一个 变量并将一个引用类型赋值给该变量的时候这个值的引用次数就加 1，如果该变量的值变成了另外一个，则这个值得引用次数减 1，当这个值的引用次数变为 0 的时 候，说明没有变量在使用，这个值没法被访问了，因此可以将其占用的空间回收，这样垃圾回收器会在运行的时候清理掉引用次数为 0 的值占用的空间
