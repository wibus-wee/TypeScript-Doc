# 5 TypeScript 函数参数和返回类型定义

## 5.1 简单类型定义

上次我们写了一个getTotal的函数，并且对传入的参数作了定义，我们再复习一遍。

新建一个文件demo5.ts,然后写入代码

```typescript
function LastgetTotal(one: number, two: number) {
    return one + two;
}
const LastTotal = LastgetTotal(1, 2);
```

代码其实有一个小坑，就是我们并没有定义getTotal的返回值类型，虽然TypeScript可以自己推断出返回值是number类型。 但是如果这时候我们的代码写错了，比如写成了下面这个样子。

```typescript
function BadgetTotal(one: number, two: number) {
    return one + two + "";
  }
  
const Badtotal = BadgetTotal(1, 2); 
```

这时候total的值就不是number类型了，但是不会报错。有的小伙伴这时候可能会说，可以直接给total一个类型注解，比如写成这个样子。

```typescript
const total: number = getTotal(1, 2);
```

这样写虽然可以让编辑器报错，但是这还不是很高明的算法，因为你没有找到错误的根本，这时错误的根本是getTotal()函数的错误，所以合适的做法是给函数的返回值加上类型注解，代码如下：

```typescript
function BettergetTotal(one: number, two: number): number {
    return one + two;
}
const BetterTotal = BettergetTotal(1, 2);
//这段代码就比较严谨了
```

## 5.2 函数无返回值时定义方法
有时候函数是没有返回值的，比如现在定义一个sayHello的函数，这个函数只是简单的terminal打印，并没有返回值。
```typescript
function sayHello() {
  console.log("hello world");
}
```
这就是没有返回值的函数，我们就可以给他一个类型注解void，代表没有任何返回值。
```typescript
function sayHello(): void {
  console.log("hello world");
}
```
如果这样定义后，你再加入任何返回值，程序都会报错。

## 5.3 never 返回值类型
如果一个函数是永远也执行不完的，就可以定义返回值为never，那什么样的函数是永远也执行不完的那?我们先来写一个这样的函数(比如执行执行的时候，抛出了异常，这时候就无法执行完了)。
```typescript
function errorFuntion(): never {
  throw new Error();
  console.log("Hello World");
}
```
还有一种是一直循环，也是我们常说的死循环，这样也运行不完，比如下面的代码：
```typescript
function forNever(): never {
  while (true) {}
  console.log("Hello ");
}
```
## 5.4 函数参数为对象(解构)时
这个坑有很多小伙伴掉下去过，就是当一个函数的参数是对象时，我们如何定义参数对象的属性类型。我先写个一般javaScript的写法。
```typescript
function add({ one, two }) {
  return one + two;
}

const total = add({ one: 1, two: 2 });
```
在浏览器中你会看到直接报错了，意思是total有可能会是任何类型，那我们要如何给这样的参数加类型注解那？最初你可能会这样写。
```typescript
function add({ one: number, two: number }) {
  return one + two;
}

const total = add({ one: 1, two: 2 });
```
你在编辑器中会看到这种写法是完全错误的。那正确的写法应该是这样的。
```typescript
function add({ one, two }: { one: number, two: number }): number {
  return one + two;
}

const three = add({ one: 1, two: 2 });
```
如果参数是对象，并且里边只有一个属性时，我们更容易写错。 错误代码如下：
```typescript
function getNumber({ one }: number) {
  return one;
}

const one = getNumber({ one: 1 });
```
看着好像没什么问题，但实际这是有问题的，正确的代码应该时这样的。
```typescript
function getNumber({ one }: { one: number }): number {
  return one;
}

const one = getNumber({ one: 1 });
```
这样写才是正确的写法

# Demo5.ts
```typescript
/**
 * Demo5.ts
 * TypeScript 函数参数和返回类型定义
 * @date 2021-1-1
 * @author Wibus
 */


// 1 复习下demo4的getTotal
function LastgetTotal(one: number, two: number) {
    return one + two;
}
const LastTotal = LastgetTotal(1, 2);
//  代码其实有一个小坑，就是我们并没有定义getTotal的返回值类型，虽然TypeScript可以自己推断出返回值是number类型。 但是如果这时候我们的代码写错了，比如写程了下面这个样子。
function BadgetTotal(one: number, two: number) {
    return one + two + "";
  }
  
const Badtotal = BadgetTotal(1, 2); //这时候total的值就不是number类型了，但是不会报错。
// 1.1 某些人的解决办法
const SomePersontotal: number = BadgetTotal(1, 2); //这样写虽然可以让编辑器报错(不能将类型“string”分配给类型“number”。)，但是这还不是很高明的算法，因为你没有找到错误的根本

// 1.2 合适的做法是给函数的返回值加上类型注解

function BettergetTotal(one: number, two: number): number {
    return one + two;
}
const BetterTotal = BettergetTotal(1, 2);
//这段代码就比较严谨了

// 2 never 返回值类型
// 如果一个函数是永远也执行不完的，就可以定义返回值为never
function errorFuntion(): never {
    throw new Error();
    console.log("Hello World");
}
// 👆执行执行的时候，抛出了异常，这时候就无法执行完了

//void 无返回值类型
function avoid(): void {
    const a = 123
    //这个时候这个函数里面是不允许return一个值的
    return a;
}

function forNever(): never {
  while (true) {}
  console.log("Hello");
}
// ⬆️死循环，这样也运行不完
```