# 21 TypeScript 类中泛型-难点

在上一节，我们讲了一下TypeScript的函数泛型的基本语法，这次我们来讲类中泛型

##  编写一个基本类

```typescript
class SelectGirl {
  constructor(private girls: string[]) {}
  getGirl(index: number): string {
    return this.girls[index];
  }
}

const selectGirl = new SelectGirl(["大脚", "刘英", "晓红"]);
console.log(selectGirl.getGirl(1));

```

写完后，可以在终端中使用`ts-node Demo.ts`进行预览，可以看到控制台中输出了`刘英`的名字。学到现在你写这样的一个类应该是非常容易的了

> 为什么是刘英，我们的程序一般排序是 0,1,2,3,4,5这样子的，这种排序方式基本所有语言都是这样的

那么如果我们想更好的保护这个名字，将会使用编号，此时上面的代码如果要这样做的话，就会变成

```typescript
class SelectGirl {
  constructor(private girls: string[] | number[]) {}
  getGirl(index:number): string | number{
    return this.girl[index];
  }
}
```

看起来很麻烦，因此我们需要使用泛型来重构代码

## 初始类的泛型

既然书接上回，那么肯定定义泛型是用`<>`，因此我们可以这个样子

```typescript
class SelectGirl<T> {
  constructor(private girls: T[]) {}
  getGirl(index: number): T {
    return this.girls[index];
  }
}
const selectGirl = new SelectGirl(["小明", "小红", "小英"])
console.log(selectGirl.getGirl(1));
```

这时候代码并不报错，也使用了泛型，但是在实例化对象的时候，TypeScript 是通过类型推断出来的。上节课已经介绍，这种方法并不好，所以还是需要在实例化对象的时候，对泛型的值进行确定，比如是`string`类型，就这样写

```typescript
const selectGirl = new SelectGirl() <string> ["小明", "小红", "小英"]
```

## 泛型中继承

如果我们要求返回的是一个对象中的name，那么将会变成这样：

```typescript
const this.girls[index].name
```

这样子的话，代码绝对会报错，传递过来的值必须是一个对象类型的，里面还必须要有一个`name`属性

这个时候就会用到`继承`了，我们可以用接口（interface）来实现。写一个`Girls`的接口，每一个接口中都要有name属性，代码就会变成这样

```typescript
interface Girls{
  name: string;
}
```

我们写了接口，就可以用`extends`才实现泛型继承

```typescript
class SelectGirl<T extends Girls>{
  
}
```

那么这样子就会变的这个泛型里面一定要有一个name属性，因为他`extends`了接口

但是但是，直到现在程序还是报错的，因为我们返回的类型不正确，应该是string才对，所以

```typescript
interface Girl {
  name: string;
}

class SelectGirl<T extends Girl> {
  // 限制了必须要有 name 属性
  constructor(private girls: T[]) {}
  getGirl(index: number): string {
    return this.girls[index].name;
  }
}

const selectGirl = new SelectGirl([
  { name: "大脚" },
  { name: "刘英" },
  { name: "晓红" },
]);
// 这个时候就不是之前的["aaa","bbb","ccc"]了
console.log(selectGirl.getGirl(1));
```

我们在`SelectGirl`中使用了类中泛型，意思是我不知道我之后将会用什么类型但是它永远会限制你有一个约束条件：name属性

## 泛型约束

这个时候这个泛型是可以是任意类型，布尔、字符串之类的。但是如果要把这个数据类型定为必须是string或者number类型的话

```typescript
class SelectGirl<T> {
  constructor(private girls: T[]) {}
  getGirl(index: number): T {
    return this.girls[index];
  }
}

const selectGirl = new SelectGirl<string>(["大脚", "刘英", "晓红"]);
console.log(selectGirl.getGirl(1));
```

然后进行约束，这时候还是使用关键字`extends`来进行约束，把代码改成下面的样子。

```typescript
class SelectGirl<T extends string | number> {
  constructor(private girls: T[]) {}
  getGirl(index: number): T {
    return this.girls[index];
  }
}

const selectGirl = new SelectGirl<string>(["大脚", "刘英", "晓红"]);
console.log(selectGirl.getGirl(1));
```

