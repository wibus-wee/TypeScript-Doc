# 4 Typescript的类型注解和类型推断

TypeScript 中的两个基本概念：`类型注解`和`类型推断`，这两个概念在我们编写 TypeScript 代码时会一直使用(重点)，但很多教程都没有讲解，不过在官方文档中有比较好的解释。你现在可能还不能完全理解我说的这两个概念，但是你看完文章后就会有很直观的了解啦

## 4.1 type annotation 类型注解

我们直接点，直接看代码

```typescript
let countDemo4: number;
countDemo4 = 123;
```

这段代码就是类型注解，意思是显示的告诉代码，我们的count变量就是一个数字类型，这就叫做类型注解

## 4.2 type inferrence 类型推断

当你明白了`类型注解`的概念之后，再学`类型推断`就更简单了，先来看一段代码。还是在Demo4.ts文件中写入下面的代码。

```typescript
let countInterfence = 123; //let countInterfence: number
```

这时候我并没有显示的告诉你变量countInference是一个`数字类型`，但是如果你把鼠标放到变量上时，你会发现 TypeScript `自动`把变量注释为了number（数字）类型，也就是说它是有某种推断能力的，通过你的代码 `TS` 会自动的去尝试`分析变量的类型`

## 4.2.1 工作使用问题（潜规则）

- 如果 `TS` 能够自动分析变量类型， 我们就什么也不需要做了
- 如果 `TS` 无法分析变量类型的话， 我们就需要使用类型注解

## 4.2.2 不需要注解例子

我们来看两个例子，先是一个不需要注解的

```typescript
const one = 123;
const two = "abc";
const three = one + two;
```

## 4.2.3 需要写的例子

```typescript
function getTotal(one, two) {
    return one + two;
  }
const total = getTotal(1, 2); //正常情况
const Warningtotal = getTotal(1, "字符串"); //非正常情况
```

这种形式，就需要用到`类型注释`了，因为这里的one和two会显示为any类型。这时候如果你传字符串，你的逻辑就是*错误*的，所以你必须加一个`类型注解`

```typescript
function GoodgetTotal(one: number, two: number) {
    return one + two;
  }
const Goodtotal = getTotal(1, 2); 
```

为什么total这个变量不需要加类型注解，因为当one和two两个变量加上注解后，TypeScript 就可以自动通过类型推断，分析出变量的类型。

## 4.2.4 推断对象中属性的类型

当然 TypeScript 也可以推断出对象中属性的类型，比如现在写一个小姐姐的对象，然后里边有两个属性。

```typescript

const XiaoJieJie = {
    name: "刘英",
    age: 18,
  };

/* 
const XiaoJieJie: {
    name: string;
    age: number;
}
 */

```

写完后你把鼠标放在XiaoJieJie对象上面，就会提示出他里边的属性，这表明 TypeScript 也分析出了对象的属性的类型。

在写 TypeScript 代码的一个重要宗旨就是每个变量，每个对象的属性类型都应该是固定的，如果你推断就让它推断，推断不出来的时候你要进行注释。

## Demo4.ts

```typescript
/**
* Demo4.ts
 * 类型注解 & 类型推断
 * @date 2021-1-1
 * @author Wibus
 * TypeScript 中的两个基本概念：类型注解和类型推断，这两个概念在我们编写 TypeScript 代码时会一直使用(重点)
 */

 // 1 type annotation 类型注解
let countDemo4: number;
countDemo4 = 123;
// 这段代码就是类型注解，意思是显示的告诉代码，我们的count变量就是一个数字类型，这就叫做类型注解

 // 2 type inferrence 类型推断
 let countInterfence = 123; //let countInterfence: number
 /**
  * 我并没有显示的告诉你变量countInference是一个数字类型，但是如果你把鼠标放到变量上时，你会发现 TypeScript 自动把变量注释为了number（数字）类型
  * 也就是说它是有某种推断能力的，通过你的代码 TS 会自动的去尝试分析变量的类型。
  * 这个就彷佛是人的情商比较高，还没等女生表白，你就已经看出她的心思🤣
  */

  /**
   * 如果 TS 能够自动分析变量类型， 我们就什么也不需要做了
   * 如果 TS 无法分析变量类型的话， 我们就需要使用类型注解
   */

// 3 不需要写注解的例子 🌰
const one = 123;
const two = "abc";
const three = one + two;

// 4 需要写的例子 🌰
function getTotal(one, two) {
    return one + two;
  }
const total = getTotal(1, 2); //正常情况
const Warningtotal = getTotal(1, "字符串"); //非正常情况
//   这种形式，就需要用到类型注释了，因为这里的one和two会显示为any类型。这时候如果你传字符串，你的逻辑就是错误的，所以你必须加一个类型注解
function GoodgetTotal(one: number, two: number) {
    return one + two;
  }
const Goodtotal = getTotal(1, 2); 
// 为什么total这个变量不需要加类型注解，因为当one和two两个变量加上注解后，TypeScript 就可以自动通过类型推断，分析出变量的类型。

// 5 推断对象中属性的类型
/* 
const XiaoJieJie: {
    name: string;
    age: number;
}
 */
const XiaoJieJie = {
    name: "刘英",
    age: 18,
  };


// 写 TypeScript 代码的一个重要宗旨就是每个变量，每个对象的属性类型都应该是固定的，如果你推断就让它推断，推断不出来的时候你要进行注释。
```