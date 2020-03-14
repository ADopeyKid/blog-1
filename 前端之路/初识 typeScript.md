## 《前端之路》 - 初试 TypeScript + Vue

### 一、先讲讲 TypeScript

> 什么是 typeScript ？

`typeScript 是 Javascript 的超集` 我们用一张图来简单介绍下 ts 和 js 清清楚楚明明白白的关系～

![](https://img2020.cnblogs.com/blog/675289/202003/675289-20200312003252090-1948582131.jpg)

> 为什么会出现 typeScript

在说 `typeScript` 之前 ，我们先了解下 Javascript。

> JS 里面一切皆为对象，通过原型链来定义了系列不同类型数据的原生方法，然后给到了系列可以改变上下文的奇淫巧技，让 JS 在使用起来的时候可以非常方便，不需要考虑过多，链上了咱们就疯狂使用，这样真的好么？（ 灵魂拷问 ）
>
> 而且在数据类型上，JS 也是没有过多的限制，只要你定了这个变量且赋值了，那么在该变量未被销毁之前，你也可以疯狂改变它的数据类型（基础数据类型）
>
> 在有了几年的开发经验之后，特别是参与过大型项目开发的同学就会发现，对于初学者来讲非常方便友好的特性，突然就变成了 bug 制造机。往往因为数据类型的判断，JS 都给出了一系列的方法，而且都还不是特别准确，这让一项严谨的开发者们变的有些不那么严谨，那么 `typeScript` 就出现了，让编程这项本来就需要非常严谨的工作，回归了本质。 这或许就是 `typeScript` 出现的原因。

> 如何使用 `typeScript`
> 如何使用的话题，其实对于有过几年的开发者来讲，最简单且最快速的学习方法就是打开 他们的官方文档，[typeScript 官方文档](https://www.typescriptlang.org/)

但是了，我在阅读过程中查到了新的版本文档，阅读起来人性化了很多，这里也奉上地址 [typeScript 官方文档-V2](https://www.typescriptlang.org/v2/docs/handbook/basic-types.html)

> 下面我们就先针对 typeScript 的基础知识来进行复习一下

### 二、 typeScript 的数据类型 （Basic Types）

> typeScript 的 Basic Types 包含了哪些呢？

- Boolean （布尔类型）
- Number （数字类型）
- String （字符串类型）
- Array （数组类型）
- Tuple （元组类型）
- Enum （可枚举类型）
- Any （任意类型）
- Void （Void 类型）
- Null & Undefined
- Never （Never 类型）
- Object （object 类型-非原始类型）

##### 2.1.1 Boolean （布尔类型）

> `TypeScript` 语法

```typescript
let isBool: Boolean = false;
```

> 被编译成 `ES5` 的 `JavaScript`

```javascript
"use strict";
var isBool = false;
```

##### 2.1.2 Number （数字类型）

> `TypeScript` 语法

```typescript
let nums: number = 123;
```

> 被编译成 `ES5` 的 `JavaScript`

```javascript
"use strict";
var nums = 123;
```

##### 2.1.3 String （字符串类型）

> `TypeScript` 语法

```typescript
let str: string = "123";
```

> 被编译成 `ES5` 的 `JavaScript`

```javascript
"use strict";
var str = "123";
```

##### 2.1.4 Array （数组类型）

> `TypeScript` 语法

```typescript
// 纯数组类型数组表示方式
let arr0: number[] = [123, 123];
// 使用数组泛型
let arr1: Array<number> = [123, 345];
let arr2: Array<string> = ["123", "345"];
let arr3: Array<any> = [123, "345", { title: "123" }];
```

> 被编译成 `ES5` 的 `JavaScript`

```javascript
"use strict";
// 纯数组类型数组表示方式
var arr0 = [123, 123];
// 使用数组泛型
var arr1 = [123, 345];
var arr2 = ["123", "345"];
var arr3 = [123, "345", { title: "123" }];
```

##### 2.1.5 Tuple （元组类型）

    稍微解释下什么叫元组类型,元组类型本质上也属于 数组类型的一种，是数组类型的子集，然后不同的一点在于，元组类型的数据长度是已知的。就是说我们为这里每一位数组中的数据定义类型。那这种类型就叫 ##元组类型##

> `TypeScript` 语法

```typescript
let tupleArr: [number, string];
tupleArr = [123, "123"];
```

> 被编译成 `ES5` 的 `JavaScript`

```javascript
"use strict";
var tupleArr;
tupleArr = [123, "123"];
```

##### 2.1.6 Enum （可枚举类型）

    稍微解释下什么叫可枚举类型，因为这对于大多数只了解 JS 的前端开发者来讲是一个新的数据类型，但是 `可枚举类型` 在 c/c#/java 中已经是非常常见的了。一句话概括就是，枚举是组织收集有关联变量的一种方式。来，我们先举个🌰：

     在 c语言中，我们需要定义一系列的变量，我们一般会这样去定义：

```basic
#define MON 1
#define TUE 2
#define WED 3
#define THU 4
.
.
.
```

    如果有了枚举类型，我们又可以怎么来定义呢？

```basic
enum DAY {
	MON=1, TUE, WED, THU, FRI, SAT, SUN
}
```

> 那就有同学要过来问了， 这样有什么区别么？这是一个好问题，因为我们来结合一个实际我们前端开发过程中经常会遇到的一个场景来描述一下枚举类型存在的必要性。

> `TypeScript` 语法

```typescript
enum HttpStutas {
  success = 200,
  error = 404,
  noRequestId = 10010,
  noRequestName = 10011
}

let res = HttpStutas.success;
console.log(res);
```

> 被编译成 `ES5` 的 `JavaScript`

```javascript
"use strict";
var HttpStutas;
(function(HttpStutas) {
  HttpStutas[(HttpStutas["success"] = 200)] = "success";
  HttpStutas[(HttpStutas["error"] = 404)] = "error";
  HttpStutas[(HttpStutas["noRequestId"] = 10010)] = "noRequestId";
  HttpStutas[(HttpStutas["noRequestName"] = 10011)] = "noRequestName";
})(HttpStutas || (HttpStutas = {}));
var res = HttpStutas.success;
console.log(res);

// 这里对于我们需要的一个理解是，在 JavaScript 赋值运算符，就是这里的等号，返回的解决是被赋的这个值。
```
