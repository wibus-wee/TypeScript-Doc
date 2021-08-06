# 7 TypeScript 元组的使用和类型约束

元组是TS特有的一个概念，JavaScript并没有这个概念

## 7.1 元组的基本使用

我们先来看一个例子

```typescript
const xiaojiejie = ["Qwq", "NoJob", 28];
```

这时候把鼠标放到xiaojiejie变量上面，可以看出`推断`出来的类型。我们就用`类型注解`的形式给他作一个注解

```typescript
const zhujie_xiaojiejie : (number | string)[] = ["Qwq", "NoJob", 28];
```

这个时候你已经添加了`类型注解`，但是在下面的代码当中会有一个`小细节问题`

```typescript
const Badxiaojiejie: (number | string)[] = ["Qwq", 28, "NoJob"];
```

我们只是把数组的位置调换了一下，但是`TS`并不能发现这个问题，所以我们需要一个更强大的类型，来解决，所以，这就是`元组`

元组和数组比较类似，但是类型注解的时候有点不一样

```typescript
const Shuzu_xiaojiejie: [string, string, number] = ["Qwq", "NoJob", 28];
```

这个样子我们就把每个类型的位置都固定住了，这就叫做元组

## 7.2 元组的使用

我们假设有这样子的一组数据

```typescript
"dajiao", "teacher", 28;
"liuying", "teacher", 18;
"cuihua", "teacher", 25;
```

如果是这个样子的话，我们可以看到前两个都是字符串，最后一个是常数。

```typescript
const xiaojiejies: [string, string, number][] = [
  ["dajiao", "teacher", 28],
  ["liuying", "teacher", 18],
  ["cuihua", "teacher", 25],
];
```

你要搞清楚元组和数组的区别，在理解后能在项目中适当的时候使用不同的类型。

## Demo7.ts

```typescript
/**
 * Demo7.ts
 * TypeScript 元组的使用和类型约束
 * @date 2021-1-2
 * @author Wibus
 */

//元组是TS特有的一个概念，JavaScript并没有这个概念

// 1 元组的基本使用
const xiaojiejie = ["Qwq", "NoJob", 28];
// 把上面的进行类型注解
const zhujie_xiaojiejie : (number | string)[] = ["Qwq", "NoJob", 28];
// 这个时候你已经添加了类型注解，但是在下面的代码当中会有一个小细节问题
const Badxiaojiejie: (number | string)[] = ["Qwq", 28, "NoJob"];
//我们只是把数组的位置调换了一下，但是TS并不能发现这个问题，所以我们需要一个更强大的类型，来解决，所以，这就是元组
const Shuzu_xiaojiejie: [string, string, number] = ["Qwq", "NoJob", 28];
// 这个时候我们就已经把每一个类型都固定住了

// 2 元组的使用

// 得到的数据源是这样子的：
// "dajiao", "teacher", 28;
// "liuying", "teacher", 18;
// "cuihua", "teacher", 25;

const xiaojiejies: [string, string, number][] = [
  ["dajiao", "teacher", 28],
  ["liuying", "teacher", 18],
  ["cuihua", "teacher", 25],
];

// 你要搞清楚元组和数组的区别，在理解后能在项目中适当的时候使用不同的类型。
```