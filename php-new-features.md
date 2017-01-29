# PHP 新特性

PHP 5.x 和最新的 PHP 7 中，不断加入了很多新特性。除去性能提升外（特别是 PHP 7），主要集中在“语法糖🍬”，提高开发效率和开发者体验。

## 特性: 命名空间 `namespace`

PHP 自 5.3 版本开始，引入了命名空间 [`namespace`](http://php.net/manual/en/language.namespaces.php)。不必多说，常见的编程语言大多有命名空间这里就不做过多叙述了。PHP 的命名空间最大的不同就是，用反斜杠作为分隔符。

```php
namespace MsbuTech\PhpBook;

use MsbuTech\PhpBook;
```

## 特性: `traits`

PHP 自 5.4 版本开始，引入了 [`traits`](http://php.net/manual/en/language.oop5.traits.php)。Traits 是一种单继承编程语言的代码复用机制。

### 用法

### `traits` 和 `interface`

`traits` 和 `interface` 都是为了解决多重继承的问题。

按照松本行弘在《松本行弘的程序世界》中所说，继承是为了避免重复的方法。但处理对象的维度可能不止一个，所以单一继承很不够的。于是，在一些编程语言中引入了多重继承，如 C++。

对于多重继承来说，会引发一些麻烦：

1. 类的关系呈复杂的网状结构
2. 继承功能（函数）名字重复

所以在一部分开发者当中评价并不好。

但为了程序的生产力，还得保持多重继承的能力。PHP 的面向对象语法和 Java 一致，也是单继承并支持 `interface`。而 `interface` 是一种对规格也可以说是函数定义的继承，并不能带来代码的复用。所以 Java 推荐使用多个对象的组合（composition）和委托（delegate）。

但历来“大杂烩”的 PHP 引入了 `traits`。

熟悉 Ruby 的朋友们肯定很熟悉 [Mix-in](https://www.wikiwand.com/en/Mixin)，traits 可以说就是 PHP 中的 Mix-in。根据松本行弘的定义：

> 用 Mix-in 做多重继承设计时，从第2个类开始的类药满足以下条件。

> 1. 不能单独生成实例的抽象类

> 2. 不能继承 Mix-in 以外的类

这些定义看起来像是一些限制，但用简单的话说，Mix-in 的中文名“混入”很传神。通过关键字 `use` 混入或者说是乱入一堆方法和变量 :)。

## 特性: 闭包

PHP 自 5.3 版本开始，引入了[闭包](http://php.net/manual/en/class.closure.php)，也就是匿名函数。

[《深入理解 PHP 内核》第四章](http://www.php-internals.com/book/?p=chapt04/04-04-anonymous-function)对此有精确的解释：

> 说到匿名函数，就不得不提到闭包了，闭包是词法闭包(Lexical Closure)的简称，是引用了自由变量的函数， 这个被引用的自由变量将和这个函数一同存在，即使离开了创建它的环境也一样，所以闭包也可认为是有函数和与其相关引用组合而成的实体。 在一些语言中，在函数内定义另一个函数的时候，如果内部函数引用到外部函数的变量，则可能产生闭包。在运行外部函数时， 一个闭包就形成了。

> 这个词和匿名函数很容易被混用，其实这是两个不同的概念，这可能是因为很多语言实现匿名函数的时候允许形成闭包。

### `use` 关键字

这是本页第三次出现 `use`，第一次是 `use` 命名空间，第二次是 `use` 一个或多个 `traits`。这里，`use` 的作用是访问上层作用域内的变量。

了解 JavaScript 的朋友可能会注意到，JavaScript 不存在这种关键字，因为 JavaScript 在函数内部可以读取上一层作用域变量。

