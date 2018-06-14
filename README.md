# Introduction

> This is the Simplified Chinese translation of [_mostly-adequate-guide_](https://github.com/DrBoolean/mostly-adequate-guide), thank Professor [Franklin Risby](https://github.com/DrBoolean) for his great work!

## 关于本书

这本书的主题是函数范式（functional paradigm），我们将使用 JavaScript 这个世界上最流行的函数式编程语言来讲述这一主题。有人可能会觉得选择 JavaScript 并不明智，因为当前的主流观点认为它是一门命令式（imperative）的语言，并不适合用来讲函数式。但我认为，这是学习函数式编程的最好方式，因为：

* **你很有可能在日常工作中使用它**

  这让你有机会在实际的编程过程中学以致用，而不是在空闲时间用一门深奥的函数式编程语言做一些玩具性质的项目。

* **你不必从头学起就能开始编写程序**

  在纯函数式编程语言中，你必须使用 monad 才能打印变量或者读取 DOM 节点。JavaScript 则简单得多，可以作弊走捷径，因为毕竟我们的目的是学写纯函数式代码。JavaScript 也更容易入门，因为它是一门混合范式的语言，你随时可以在感觉吃力的时候回退到原有的编程习惯上去。

* **这门语言完全有能力书写高级的函数式代码**

  只需借助一到两个微型类库，JavaScript 就能模拟 Scala 或 Haskell 这类语言的全部特性。虽然面向对象编程（Object-oriented programing）主导着业界，但很明显这种范式在 JavaScript 里非常笨拙，用起来就像在高速公路上露营或者穿着橡胶套鞋跳踢踏舞一样。我们不得不到处使用 `bind` 以免 `this` 不知不觉地变了，语言里没有类可以用（目前还没有），我们还发明了各种变通方法来应对忘记调用 `new` 关键字后的怪异行为，私有成员只能通过闭包（closure）才能实现，等等。对大多数人来说，函数式编程看起来更加自然。

以上说明，强类型的函数式语言毫无疑问将会成为本书所示范式的最佳试验场。JavaScript 是我们学习这种范式的一种手段，将它应用于什么地方则完全取决于你自己。幸运的是，所有的接口都是数学的，因而也是普适的。最终你会发现你习惯了 swiftz、scalaz、haskell 和 purescript，以及其他各种数学偏向的语言。

#### Gitbook \(更好的阅读体验\)

* [在线阅读](https://llh911001.gitbooks.io/mostly-adequate-guide-chinese/content/)
* [下载EPUB](https://www.gitbook.com/download/epub/book/llh911001/mostly-adequate-guide-chinese)
* [下载Mobi \(Kindle\)](https://www.gitbook.com/download/mobi/book/llh911001/mostly-adequate-guide-chinese)

#### 练习题

你可以在 [ScriptOJ](https://scriptoj.com/problemsGroups/593a584f36387a3df1d87422) 在线进行本书的编程练习（by [@胡子大哈](https://github.com/huzidaha)）。

## 目录

### 第 1 部分

* [第 1 章: 我们在做什么？](di-1-zhang-wo-men-zai-zuo-shi-mo/)
  * [介绍](di-1-zhang-wo-men-zai-zuo-shi-mo/#介绍)
  * [一个简单例子](di-1-zhang-wo-men-zai-zuo-shi-mo/#一个简单例子)
* [第 2 章: 一等公民的函数](di-2-zhang-yi-deng-gong-min-de-han-shu/)
  * [快速概览](di-2-zhang-yi-deng-gong-min-de-han-shu/#快速概览)
  * [为何钟爱一等公民](di-2-zhang-yi-deng-gong-min-de-han-shu/#为何钟爱一等公民)
* [第 3 章: 纯函数的好处](di-3-zhang-chun-han-shu-de-hao-chu/)
  * [再次强调“纯”](di-3-zhang-chun-han-shu-de-hao-chu/#再次强调“纯”)
  * [副作用可能包括...](di-3-zhang-chun-han-shu-de-hao-chu/#副作用可能包括)
  * [八年级数学](di-3-zhang-chun-han-shu-de-hao-chu/#八年级数学)
  * [追求“纯”的理由](di-3-zhang-chun-han-shu-de-hao-chu/#追求“纯”的理由)
  * [总结](di-3-zhang-chun-han-shu-de-hao-chu/#总结)
* [第 4 章: 柯里化（curry）](di-4-zhang-ke-li-hua-curry/)
  * [不可或缺的 curry](di-4-zhang-ke-li-hua-curry/#不可或缺的-curry)
  * [不仅仅是双关语／咖喱](di-4-zhang-ke-li-hua-curry/#不仅仅是双关语咖喱)
  * [总结](di-4-zhang-ke-li-hua-curry/#总结)
* [第 5 章: 代码组合（compose）](di-5-zhang-dai-ma-zu-he-compose/)
  * [函数饲养](di-5-zhang-dai-ma-zu-he-compose/#函数饲养)
  * [pointfree](di-5-zhang-dai-ma-zu-he-compose/#pointfree)
  * [debug](di-5-zhang-dai-ma-zu-he-compose/#debug)
  * [范畴学](di-5-zhang-dai-ma-zu-he-compose/#范畴学)
  * [总结](di-5-zhang-dai-ma-zu-he-compose/#总结)
* [第 6章: 示例应用](di-6-zhang-shi-li-ying-yong/)
  * [声明式代码](di-6-zhang-shi-li-ying-yong/#声明式代码)
  * [一个函数式的 flickr](di-6-zhang-shi-li-ying-yong/#一个函数式的-flickr)
  * [有原则的重构](di-6-zhang-shi-li-ying-yong/#有原则的重构)
  * [总结](di-6-zhang-shi-li-ying-yong/#总结)

### 第 2 部分

* [第 7 章: Hindley-Milner 类型签名](di-7-zhang-hindleymilner-lei-xing-qian-ming/)
  * [初识类型](di-7-zhang-hindleymilner-lei-xing-qian-ming/#初识类型)
  * [神秘的传奇故事](di-7-zhang-hindleymilner-lei-xing-qian-ming/#神秘的传奇故事)
  * [缩小可能性范围](di-7-zhang-hindleymilner-lei-xing-qian-ming/#缩小可能性范围)
  * [自由定理](di-7-zhang-hindleymilner-lei-xing-qian-ming/#自由定理)
  * [总结](di-7-zhang-hindleymilner-lei-xing-qian-ming/#总结)
* [第 8 章: 特百惠](di-8-zhang-te-bai-hui/)
  * [强大的容器](di-8-zhang-te-bai-hui/#强大的容器)
  * [第一个 functor](di-8-zhang-te-bai-hui/#第一个-functor)
  * [薛定谔的 Maybe](di-8-zhang-te-bai-hui/#薛定谔的-maybe)
  * [“纯”错误处理](di-8-zhang-te-bai-hui/#“纯”错误处理)
  * [王老先生有作用...](di-8-zhang-te-bai-hui/#王老先生有作用)
  * [异步任务](di-8-zhang-te-bai-hui/#异步任务)
  * [一点理论](di-8-zhang-te-bai-hui/#一点理论)
  * [总结](di-8-zhang-te-bai-hui/#总结)
* [第 9 章: Monad](di-9-zhang-monad/)
  * [pointed functor](di-9-zhang-monad/#pointed-functor)
  * [混合比喻](di-9-zhang-monad/#混合比喻)
  * [chain 函数](di-9-zhang-monad/#chain-函数)
  * [理论](di-9-zhang-monad/#理论)
  * [总结](di-9-zhang-monad/#总结)
* [第 10 章: Applicative Functor](di-10-zhang-applicative-functor/)
  * [应用 applicative functor](di-10-zhang-applicative-functor/#应用-applicative-functor)
  * [瓶中之船](di-10-zhang-applicative-functor/#瓶中之船)
  * [协调与激励](di-10-zhang-applicative-functor/#协调与激励)
  * [lift](di-10-zhang-applicative-functor/#lift)
  * [免费开瓶器](di-10-zhang-applicative-functor/#免费开瓶器)
  * [定律](di-10-zhang-applicative-functor/#定律)
  * [总结](di-10-zhang-applicative-functor/#总结)

## 未来计划

* 第 1 部分是基础知识。这是初版草稿，所以我会及时更正发现的的错误。欢迎提供帮助！
* 第 2 部分讲述类型类（type class），比如 functor 和 monad，最后会讲到到 traversable。我希望能塞进来一些 monad transformer 相关的知识，再写一个纯函数的应用。
* 第 3 部分将开始游走于编程实践与学院学究之间。我们将学习 comonad、f-algebra、free monad、yoneda 以及其他一些范畴学概念。

