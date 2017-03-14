第1题
>
```
function sidEffecting(ary) {
  ary[0] = ary[2];
}
function bar(a,b,c) {
  c = 10
  sidEffecting(arguments);
  return a + b + c;
}
bar(1,1,1)
```

这是一个大坑, 尤其是涉及到 ES6语法的时候

知识点:

* [function.arguments ](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/arguments)

首先 The arguments object is an Array-like object corresponding to the arguments passed to a function.

也就是说 arguments 是一个 object, c 就是 arguments[2], 所以对于 c 的修改就是对 arguments[2] 的修改.

所以答案是 21.

然而!!!!!!

当函数参数涉及到 any rest parameters, any default parameters or any destructured parameters 的时候, 这个 arguments 就不在是一个 mapped arguments object 了…..

请看:
>
```
function sidEffecting(ary) {
  ary[0] = ary[2];
}
function bar(a,b,c=3) {
  c = 10
  sidEffecting(arguments);
  return a + b + c;
}
bar(1,1,1)
```

答案是 12 !!!!
