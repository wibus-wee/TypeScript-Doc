# 20 TypeScript 函数泛型 - 难点

泛型我个人认为是 TypeScript 的一个难点，我第一次学完后根本不能完全理解

## 联合类型 Demo

先写一个`join`方法，方法需要接受两个参数: `first`, `second`，并且参数有可能是字符串类型，也可能是数字类型

```ts
function join (first: string|number, second: string|number) {
  return `${first}${second}`
}
join('I'm', 'wibus')
```

上面的代码是完全没有问题的，但是现在出现了一个需求，这就`first`的参数如果是一个字符串的话，要求`second`也必须要是字符串，反之亦然

那之前所说的都是无法解决的啦，因此就出现了一个东西：`generic` —— 泛型

## 初始泛型-generic

泛型的定义使用`<>`，比如说给我们之前的`join`方法加一个泛型，名字就叫做`type`，这个名字是可以随意选择的，但是在实际项目中必须要语义化，毕竟需要做到代码规范我觉得才能算是好代码

```ts
function join <type> (first: type, second: type) {
  return `${first}${second}`
}
join<string>('I'm', 'wibus')
```

如果要是number的话，就只需要`join<number>(123, 345)`

## 泛型中数组的使用

如果传递过来的值要求是数字，如何用泛型进行定义那?两种方法，第一种是直接使用`[]`，第二种是使用`Array<泛型>`。形式不一样，其他的都一样。

第一种写法:

```ts
function myFun<ANY>(params: ANY[]) {
  return params;
}
myFun < string > ["123", "456"];
```

第二种写法:

```ts
function myFun<ANY>(params: Array<ANY>) {
  return params;
}
myFun < string > ["123", "456"];
```

在实际项目中，我们经常使用`<T>`来作泛型的表示，当然这不是硬性的规定，只是大部分程序员的习惯性写法

## 多个泛型的定义

一个函数可以定义多个泛型，比如说我们要做俩泛型，第一个用`T`，第二批`P`

```ts
function join <T, P> (first: T, second: P) {
  return `${first}${second}`
}
join<number, string>(123, 'wibus')
```

当然也可以使用类型推断

```ts
function join <T, P> (first: T, second: P) {
  return `${first}${second}`
}
join(123, 'wibus')
// 自动推断为 number, string
```

但是我并不建议你在项目中大量使用类型推断吗，这种将不利于阅读



