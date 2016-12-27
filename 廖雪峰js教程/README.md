# 廖雪峰 js教程
> [JavaScript教程](http://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/00143449921138898cdeb7fc2214dc08c6c67827758cd2f000)

我的练习基本是按着教程敲了一遍.  用的Chrome调试窗口,很方便!

## 以下是笔记
- javascript的五种基本数据类型: Undefined，Null，Boolean，Number和String; 此外还含有一种复杂数据类型—Object
- if判断,传参传的非boolean类型
```
var s = '123';
if (s.length) { // 条件计算结果为3
    console.log("你好啊"); //打印结果为你好啊
}
原因: JavaScript把null、undefined、0、NaN和空字符串''视为false，其他值一概视为true，因此上述代码条件判断的结果是true。
```

- Map和Set是ES6标准新增的数据类型，请根据浏览器的支持情况决定是否要使用。
```
var m = new Map([['Michael', 95], ['Bob', 75], ['Adam', 85]]);
m.get('Michael'); // 95
m.delete('Adam'); // 删除key 'Adam'

var s = new Set();
s.add(1); // Set {1}
s.add(2); // Set {1, 2}
s.add(3); // Set {1, 2,3}
s.delete(3); // Set {1, 2}
```

- ES6标准引入了新的iterable类型，Array、Map和Set都属于iterable类型。
```
// 更好的方式是直接使用`iterable`内置的`forEach`方法，它接收一个函数，每次迭代就自动回调该函数。以Array为例：
//forEach()方法是ES5.1标准引入的
var a = ['A', 'B', 'C'];
a.forEach(function (element, index, array) {
    // element: 指向当前元素的值
    // index: 指向当前索引
    // array: 指向Array对象本身
    alert(element);
});

或者:
//由于JavaScript的函数调用不要求参数必须一致，因此可以忽略它们。例如，只需要获得Array的element：
var a = ['A', 'B', 'C'];
a.forEach(function (element) {
    alert(element);
});
```

- JavaScript还有一个免费赠送的关键字arguments，它只在函数内部起作用，并且永远指向当前函数的调用者传入的所有参数。arguments类似Array但它不是一个Array：

```
arguments，你可以获得调用者传入的所有参数
实际上arguments最常用于判断传入参数的个数。你可能会看到这样的写法：
// foo(a[, b], c)
// 接收2~3个参数，b是可选参数，如果只传2个参数，b默认为null：
function foo(a, b, c) {
    if (arguments.length === 2) {
        // 实际拿到的参数是a和b，c为undefined
        c = b; // 把b赋给c
        b = null; // b变为默认值
    }
    // ...
}
要把中间的参数b变为“可选”参数，就只能通过arguments判断，然后重新调整参数并赋值。
```