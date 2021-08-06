# 2 Typescript静态类型

## 2.1 一般静态类型

下面的代码是一般的，也是最简单的变量静态类型

```typescript
 // 1 一般的静态类型
 const count: number = 1; //此时number这个变量值为0
```

这里的: number就是定义了一个静态类型。

这样定义后count这个变量在程序中就永远都是数字类型了，不可以改变了。

比如我们这时候给count复制一个字符串，它就报错了。

```typescript
// 错误示范
const count: number = 1
count = "Wibus"; //这里的代码VSC将会报错提示：Cannot assign to 'count' because it is a constant.（无法分配到 "count" ，因为它是常数。）
```

你也可以发现这时候的count变量,可以使用number类型上所有的属性和方法。

当然我们还可以使用其他的类型，如string（字符串）

## 2.2 自定义静态类型

下面的代码展示了什么是 自定义静态类型

```typescript
//2 自定义静态类型
interface Student {
  name: string; //string - 字符串;
  age: number; //number 常数
}
const Ming: Student = {
  name: "小明", //可以填写字符串
  age: 14, //只能填写数字
};
```

`interface` 是我们之后需要学到的接口，这部分暂时不说

这时候你如果声明变量，跟自定义不一样，VSCode直接就会报错。需要注意的是，这时候Ming变量也具有name和age属性了。

你需要记住的是，如果使用了静态类型，不仅意味着变量的类型不可以改变，还意味着类型的属性和方法也跟着确定了。这个特点就大大提高了程序的健壮性，并且编辑器这时候也会给你很好的语法提示，加快了你的开发效率。

## Demo2.ts

```typescript
/**
 * Demo2.ts
 * 介绍typescript的静态类型
 * @date 2021-1-1
 * @author Wibus
 */

 // 1 一般的静态类型
 const count: number = 1; //此时number这个变量值为0

/**
  * 这里的: number就是定义了一个静态类型。
  * 这样定义后count这个变量在程序中就永远都是数字类型了，不可以改变了。
  * 比如我们这时候给count复制一个字符串，它就报错了。
  * count = "Wibus";
  */

count = "Wibus"; //这里的代码VSC将会报错提示：Cannot assign to 'count' because it is a constant.（无法分配到 "count" ，因为它是常数。）

//2 自定义静态类型
interface Student {
  name: string; //String - 字符串;
  age: number; //number 常数
}
const Ming: Student = {
  name: "小明", //可以填写字符串
  age: 14, //只能填写数字
};
//这时候你如果声明变量，跟自定义不一样，VSCode直接就会报错。需要注意的是，这时候Ming变量就变得具有name和age属性了

/**
 * 如果使用了静态类型，不仅意味着变量的类型不可以改变，还意味着类型的属性和方法也跟着确定了。
 * 这个特点就大大提高了程序的健壮性，并且编辑器这时候也会给你很好的语法提示，加快了你的开发效率。
 */
```

#