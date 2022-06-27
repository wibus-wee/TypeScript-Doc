# 3 Typescript 基础静态类型和对象类型

在 TypeScript 静态类型分为两种，一种是基础静态类型，一种是对象类型

## 3.1 基础静态类型

基础静态类型非常的简单，只需要在变量名后加上 *:* 之后加上类型名即可，例子如下：

```typescript
const counter : number = 918; // 类型 number only数字
const myName : string = "Wibus"; // 类型 string only字符串
```

类型不止这些，还有`null`,`undefinde`,`symbol`,`boolean`，`void`，`nerver`这些都是最常用的基础数据类型

## 3.2 对象类型

先来看一个例子，通过例子有经验的小伙伴就知道个大概了，然后我们再来讲解(其实上节课我们也讲到了，我们这里就当复习了)。

新建一个文件`demo3.ts`（你可以跟我不一样）,然后写下如下代码。

## 3.2.1 最简单的对象类型
```typescript
const xiaoGeGe: {
    name: string, //字符串类型
    age: number, //常数类型
  } = {
    name: "Wibus", //对应的数据
    age: 14,
  };
  console.log(xiaoGeGe.name);
```

写完后，我们在 **terminal（终端）** 中输入`ts-node demo3.ts`，可以看到结果输出了Wibus。这就是一个经典的对象类型，也是最简单的对象类型。

## 3.2.2 数组对象类型

对象类型也可以是数组，比如现在我们需要很多小姐姐，我们就可以这样写。

```typescript
const xiaoJieJies : string[] = ["Awa", "Qwq", "老婆"];
```

这时候的意思是，变量xiaoJieJies必须是一个数组，数组里的内容必须是字符串。你可以试着把字符串改为数字，VSCode会直接给我们报错。

```typescript
// ⚠️错误示范
const ErrorxiaoJieJies : string[] = [123, "Qwq", "老婆"]; //VSC将会直接报错
```

## 3.2.3 类类型

来看看下面的代码。这个代码就是用类的形式，来定义变量。

```typescript
class Person {} //定义一个Person类
const Js: Person = new Person();
```

这个意思就是dajiao必须是一个Person类对应的对象才可以。

## 3.2.4 函数类型

我们还可以定义一个函数类型，并确定返回值。代码如下：

```typescript
const Wibus : () => string = () => {
    return "I'm Wibus";
};
```

我们现在总结一下对象类型可以有几种形式：

- 对象类型
- 数组类型
- 类类型
- 函数类型

这几种形式我们在TypeScript里叫做对象类型。

## Demo3.ts

```typescript
/**
 * Demo3.ts
 * 基础静态类型和对象类型
 * @Date 2021-1-1
 * @author Wibus
 */


// 基础静态类型
const counter : number = 918;
const myName : string = "Wibus";
// null,undefinde,symbol,boolean，void这些都是最常用的基础数据类型

// 对象类型
// 1 🌰
const xiaoGeGe: {
    name: string, //字符串类型
    age: number, //常数类型
  } = {
    name: "Wibus", //对应的数据
    age: 14,
  };
  console.log(xiaoGeGe.name);
// ts-node Demo3.ts Result: Wibus
// 这就是一个经典的对象类型，也是最简单的对象类型。

// 2 🌰 对象类型也可以是数组
const xiaoJieJies : string[] = ["Awa", "Qwq", "老婆"]; 
// 这时候的意思是，变量xiaoJieJies必须是一个数组，数组里的内容必须是字符串。你可以试着把字符串改为数字，VSCode会直接给我们报错。
// ⚠️错误示范
const ErrorxiaoJieJies : string[] = [123, "Qwq", "老婆"]; //VSC将会直接报错

// 3 类

class Person {} //定义一个Person类
const Js: Person = new Person(); // 这个意思就是Js必须是一个Person类对应的对象才可以
// 我们还可以定义一个函数类型，并确定返回值
const Wibus : () => string = () => {
    return "I'm Wibus";
};
/**
 * 对象类型可以有几种形式：
 * 对象类型
 * 数组类型
 * 类类型
 * 函数类型
 * 这几种形式在TypeScript里叫做对象类型。
 */
```