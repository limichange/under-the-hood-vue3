首先`Object.create`的作用是将一个已经存在的对象当做原型来创建一个新的对象。

我们常常看到有人这么写。

```js
let object1 = Object.create(null)
```

这时候就有人会困惑。

```js
let object2 = {}
```

这俩不一样吗？

首先，肯定是不一样的。至于为什么，看一下原理就明白了。

我把MDN上的`ployfill1拿来，我们看看是如何实现的。

```js
Object.create = function (proto, propertiesObject) {
  // propertiesObject 是创建的时候添加属性用的，我们不用管

  function F() {}
  F.prototype = proto;
  return new F();
}
```

这是我精简过的。

这需要你对原型链有一些认识，如果你不太懂的话，需要先去看看原型链。

ok，也就是说，把传进来的对象当做原型来创建了一个新对象。

你会想为啥不直接new？

当然可以，前提是传进来的是个原型才行，如果是这样的话，那么下面这个例子就是相等的。

```js
new Constructor()
// 等于
Object.create(Constructor.prototype)
```

如果传进来的是个object，那么这个转化过程就是必要的。

那么最初的问题就很好理解了。

```js
let object1 = {}
// 等于
let object2 = Object.create(Object.prototype)
// 等于
let object3 = new Object()

let object4 = Object.create(null)
```

所以`object4`创建出来就是一个纯的对象了。

是不是很神奇？（笑

这个函数还可以轻松的实现js的继承，这里就不多讲了，有兴趣可以自己看看。

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create
