# 8 TypeScript 的 interface接口

TypeScript的接口。就是用来规范类型的

## 8.1 Interface 接口初步了解

我们要作一个简历的自动筛选程序，很简单。年龄小于 25 岁，胸围大于 90 公分的，可以进入面试环节。我们最开始的写法是这样的

```typescript
const screenresume = (name: string, age: number, bust: number) => {
    age < 24 && bust >= 90 && console.log(name + "Pass");
    age > 24 || (bust < 90 && console.log(name + "Can't Pass"));
};

screenresume("Wibus", 14, 90);
```

好像还不错，我们再加上个查看简历的功能，于是你的代码是这样

```typescript
const getResume = (name: string, age: number, bust: number) => {
    console.log(name+ "age: " + age);
    console.log(name+ "Bust: " + bust);
}
getResume("Wibus", 14, 90);
```

但是这个时候会发现，有很多东西重复了，程序开发中一直强调“代码重用”，两个方法用的类型注解一样，需要作个统一的约束。大上节课我们学了一个`类型别名`的知识可以解决代码重复的问题，这节课我们就学习一个更常用的语法`接口`（Interface）.

我们可以把这两个重复进行类型注解，定义成统一的接口。代码如下

```typescript
interface Girl {
  name: string;
  age: number;
  bust: number;
}
```

有了这个接口后我们程序也要做一些修改

```typescript
const screenresume2 = (girl: Girl) => {
    girl.age < 24 && girl.bust >= 90 && console.log(girl.name + "Pass");
    girl.age > 24 || (girl.bust < 90 && console.log(girl.name + "Can't Pass"));
};

const getResume2 = (girl: Girl) => {
    console.log(girl.name+ "age: " + girl.age);
    console.log(girl.name+ "Bust: " + girl.bust);
};

const girl = {
    name: "Wibus",
    age: 14,
    bust: 94,
};

screenresume2(girl);
getResume2(girl);
```
这样就更像是面向对象编程了,以后再用到同样的接口也不怕了，直接使用girl就可以了。

## 8.2 接口和类型别名的区别

现在我们学了`接口`，也学过了`类型别名`，这两个语法和用处好像一样, 确实用起来基本一样，但是也有少许的不同。

> 类型别名可以直接给类型，比如string，而接口必须代表对象。

比如我们的类型别名可以写出下面的代码：
```typescript
type Girl1 = stirng;
```
但是接口就不能这样写，它必须代表的是一个对象，也就是说，你初始化`girl`的时候，必须写出下面的形式.
```typescript
const girl = {
  name: "大脚",
  age: 18,
  bust: 94,
};
```

## 8.3 接口非必选值定义

我们要求尽量能看到小姐姐的腰围，但是不作强制要求，就是`可选值`。那接口如何定义？`typeScript`已经为我们准备好了相应的办法，就是在 *:* 号前加一个 *?*

比如把Girl的接口写成这样。

```typescript
interface Girl2 {
  name: string;
  age: number;
  bust: number;
  waistline?: number; // 非必选值
}
```

再修改一下getResume方法，写成这样。

```typescript
const getResume3 = (girl: Girl2) => {
  console.log(girl.name + "年龄是：" + girl.age);
  console.log(girl.name + "胸围是：" + girl.bust);
  girl.waistline && console.log(girl.name + "腰围是：" + girl.waistline);
};
```

这时候在定义`girl对象`的时候，就可以写`saistline`（腰围），也可以不写了。

## Demo8.ts

```typescript
/**
 * Demo8.ts
 * TypeScript 的 interface 接口
 * @date 2021-1-2
 * @author Wibus
 * interface东西比较多，分两次讲述
 */

// 1 interface 接口初步了解

// 1.1 简历工具
const screenresume = (name: string, age: number, bust: number) => {
    age < 24 && bust >= 90 && console.log(name + "Pass");
    age > 24 || (bust < 90 && console.log(name + "Can't Pass"));
};

screenresume("Wibus", 14, 90);
// ts-node demo8.ts
// 进入面试


const getResume = (name: string, age: number, bust: number) => {
    console.log(name+ "age: " + age);
    console.log(name+ "Bust: " + bust);
}

// 但是似乎name: string, age: number, bust: number一直在出现
// 为了避免啊代码重用，我们可以使用接口

interface Girl {
    name: string;
    age: number;
    bust: number;
}
// 于是我们就需要修改一点程序
const screenresume2 = (girl: Girl) => {
    girl.age < 24 && girl.bust >= 90 && console.log(girl.name + "Pass");
    girl.age > 24 || (girl.bust < 90 && console.log(girl.name + "Can't Pass"));
};

const getResume2 = (girl: Girl) => {
    console.log(girl.name+ "age: " + girl.age);
    console.log(girl.name+ "Bust: " + girl.bust);
};

const girl = {
    name: "Wibus",
    age: 14,
    bust: 94,
};

screenresume2(girl);
getResume2(girl);

// 2 接口和类型别名的区别

type Girl1 = string;

const girl1 = {
    name: "Wibus",
    age: 14,
    bust: 94 
};

// 3 接口非必选值定义

interface Girl2 {
  name: string;
  age: number;
  bust: number;
  waistline?: number; // 非必选值
}

const getResume3 = (girl: Girl2) => {
  console.log(girl.name + "年龄是：" + girl.age);
  console.log(girl.name + "胸围是：" + girl.bust);
  girl.waistline && console.log(girl.name + "腰围是：" + girl.waistline);
};

//这时候在定义girl对象的时候，就可以写saistline（腰围），也可以不写了。
```