# 6 TypeScript 中数组类型的定义
TypeScript 中的数组类型，一般的数组类型定义我们已经接触过了，只是没有单独拿出来讲，所以先来复习一下。

## 6.1 一般数组类型的定义

我们我们先定义一个最最最简单的数组

```typescript
const numberArr = [1,2,3]'
```

这时候你把鼠标放在`numberArr`上面可以看出，这个数组的类型就是 *number* 类型。这是 TypeScript 通过`类型推断`自己推断出来的。 如果你要显示的`注解`，也非常简单，可以写成下面的形式。
```typescript
const numberArr: number[] = [1, 2, 3];
```
同样道理，如果你的数组各项是字符串，你就可以写成这样
```typescript
const stringArr: string[] = ["a", "b", "c"];
```
也就是说你可以定义任意类型的数组，比如是`undefined`
```typescript
const undefinedArr: undefined[] = [undefined, undefined];
```

这时候问题来了，如果数组中有多种类型，比如既有数字类型，又有字符串的时候。那我们要如何定义那。 很简单，只要加个()，然后在里边加上|就可以了，具体看代码。

```typescript
const arr: (number | string)[] = [1, "string", 2];
```
数组简单类型的定义就是这样了，并不难。

## 6.2 数组中对象类型的定义

在实际项目当中肯定会有对象出现，那这个时候定义的话就麻烦一点点了

```typescript
const xiaoJieJiesDemo6: {name: string, age: number}[] = [
    {name: "Ming", age: 15},
    {name: "Wibus", age: 14},
];
```

这样子的形式看起来比较复杂，当然这段程序是可以的，但是不好读嘛

## 6.2.1 Type Alias 类型别名

`TS` 为我们弄了一个`类型别名`，使用type+名字，具体看代码

```typescript
type lady = {name: string, age: number};

const GoodxiaoJieJiesDemo6: lady[] = [
    {name: "Ming", age: 15},
    {name: "Wibus", age: 14},
];
```
这样子就好读多了

## 6.2.2 Class定义

当然，使用class来定义也是可以的，例如这样子

```typescript
class ladys{
    name: string;
    age: number;
};
const GoodxiaoJieJiesDemo6_2: ladys[] = [
    {name: "Ming", age: 15},
    {name: "Wibus", age: 14},   
];
```

我们可以看到，是可以的~

## Demo6.ts

```typescript
/**
 * Demo6.ts
 * TypeScript 中数组类型的定义
 * @date 2021-1-2
 * @author wibus
 */

// 1 一般数组类型的定义
const numberArr = [1,2,3];
// 这是最简单的数组类型（number) 当你鼠标放上变量名时，就可以看得出来是number类型（类型推断）
const numberArr2: number[] = [1,2,3];
// 类型注解
const stringArr: string[] = ["a","b","c"];
// 所以说你可以定义任何类型的数组
const undefinedArr: undefined[] = [undefined, undefined];
// 1.1 多种数据类型
const arr: (number|string)[] = [1,2,"abc"];
// 数组简单类型定义就这样了，其实不难

// 2 数组中对象类型的定义
// 在实际项目当中肯定会有对象出现，那这个时候定义的话就麻烦一点点了

const xiaoJieJiesDemo6: {name: string, age: number}[] = [
    {name: "Ming", age: 15},
    {name: "Wibus", age: 14},
];
//这样子的形式看起来比较复杂，当然这段程序是可以的，但是不好读嘛

// 2.1 Type Alias 类型别名

type lady = {name: string, age: number};
const GoodxiaoJieJiesDemo6: lady[] = [
    {name: "Ming", age: 15},
    {name: "Wibus", age: 14},
];
//这样子就好读多了

// 2.2 使用class
// 当然，使用class来定义也是可以的，例如这样子
class ladys{
    name: string;
    age: number;
};
const GoodxiaoJieJiesDemo6_2: ladys[] = [
    {name: "Ming", age: 15},
    {name: "Wibus", age: 14},   
]
// 我们可以看到，是可以的~
```