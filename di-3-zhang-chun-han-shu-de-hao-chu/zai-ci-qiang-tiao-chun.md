# 再次强调“纯”

首先，我们要厘清纯函数的概念。

> 纯函数是这样一种函数，即相同的输入，永远会得到相同的输出，而且没有任何可观察的副作用。

比如 `slice` 和 `splice`，这两个函数的作用并无二致——但是注意，它们各自的方式却大不同，但不管怎么说作用还是一样的。我们说 `slice` 符合_纯_函数的定义是因为对相同的输入它保证能返回相同的输出。而 `splice` 却会嚼烂调用它的那个数组，然后再吐出来；这就会产生可观察到的副作用，即这个数组永久地改变了。

```javascript
var xs = [1,2,3,4,5];

// 纯的
xs.slice(0,3);
//=> [1,2,3]

xs.slice(0,3);
//=> [1,2,3]

xs.slice(0,3);
//=> [1,2,3]


// 不纯的
xs.splice(0,3);
//=> [1,2,3]

xs.splice(0,3);
//=> [4,5]

xs.splice(0,3);
//=> []
```

在函数式编程中，我们讨厌这种会_改变_数据的笨函数。我们追求的是那种可靠的，每次都能返回同样结果的函数，而不是像 `splice` 这样每次调用后都把数据弄得一团糟的函数，这不是我们想要的。

来看看另一个例子。

```javascript
// 不纯的
var minimum = 21;

var checkAge = function(age) {
  return age >= minimum;
};


// 纯的
var checkAge = function(age) {
  var minimum = 21;
  return age >= minimum;
};
```

在不纯的版本中，`checkAge` 的结果将取决于 `minimum` 这个可变变量的值。换句话说，它取决于系统状态（system state）；这一点令人沮丧，因为它引入了外部的环境，从而增加了认知负荷（cognitive load）。

这个例子可能还不是那么明显，但这种依赖状态是影响系统复杂度的罪魁祸首（[http://www.curtclifton.net/storage/papers/MoseleyMarks06a.pdf](http://www.curtclifton.net/storage/papers/MoseleyMarks06a.pdf) ）。输入值之外的因素能够左右 `checkAge` 的返回值，不仅让它变得不纯，而且导致每次我们思考整个软件的时候都痛苦不堪。

另一方面，使用纯函数的形式，函数就能做到自给自足。我们也可以让 `minimum` 成为一个不可变（immutable）对象，这样就能保留纯粹性，因为状态不会有变化。要实现这个效果，必须得创建一个对象，然后调用 `Object.freeze` 方法：

```javascript
var immutableState = Object.freeze({
  minimum: 21
});
```
