
首先这个东西和string, number, bigint, boolean, null, undefined, 一样是基础类型，一个地位。不是对象也没有函数方法。

我们通过`Symbol()`来生成一个symbol，别用new，他是个函数不是构造函数，用就会报错。
返回的值很有意思，是一个唯一值，你可以当成id来理解，只不过他不是字符串或者数字组成的。这也是最主要的作用。

```js
Symbol('foo') === Symbol('foo'); // false
```

传进去的`foo`是一种描述，写不写区别不大。

有兴趣的话，非常细的部分看这些地方。

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol

https://developer.mozilla.org/en-US/docs/Glossary/Symbol
