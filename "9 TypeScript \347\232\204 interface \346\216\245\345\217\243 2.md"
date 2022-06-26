# 9 TypeScript 的 interface 接口 2

我们接着继续讲接口，接口部分的内容还是比较多的

## 9.1 允许加入任意值

简历一般是有自由发挥的空间的，所以这时候需要一些任意值，就是自己愿意写什么就写什么。这时候interface接口也是支持的。

```typescript
interface Girl1 {
    name: string;
    age: number;
    bust: number;
    waistline?: number;
    [propname: string]: any; //属性的名字是字符串类型，属性的值可以是任何类型。
  }
```

`propname` 你可以随意改成其他的名字～

这时候我们在对象里给一个性别

```typescript
const girl = {
    name: "大脚",
    age: 18,
    bust: 94,
    waistline: 21,
    sex: "女",
  };
```

再修改一下代码，就没有错误了。

```typescript
const getResume = (girl: Girl1) => {
    console.log(girl.name + "年龄是：" + girl.age);
    console.log(girl.name + "胸围是：" + girl.bust);
    girl.waistline && console.log(girl.name + "腰围是：" + girl.waistline);
    girl.sex && console.log(girl.name + "性别是：" + girl.sex);
  };
```

这时候我们的程序是不报错的，但是如果我们去掉刚才的设置，就会报错。

```typescript
[propname:string]:any;  //去掉
```

## 9.2 接口里的方法

接口里不仅可以存属性，还可以存方法，比如这时候有个`say()`方法，返回值是`string`类型。这时候你就不要再想成简历了，你需要更面向对象化的编程，想象成一个人。

```typescript
interface Girl2 {
    name: string;
    age: number;
    bust: number;
    waistline?: number;
    [propname: string]: any;
    say(): string;
}
```

加上这个`say()`方法后，程序马上就会报错，因为我们对象里没有` say `方法。那我们就要给对象一个` say `方法

```typescript
const girl2 = {
  name: "Wibus",
  age: 14,
  bust: 94,
  waistline: 21,
  sex: "女",
  say() {
    return "欢迎光临 ，红浪漫洗浴！！";
  },
};
```

## 9.3 接口和类的约束

` JavaScript `从ES6里是有类这个概念的，类可以和接口很好的结合

```typescript
class XiaoJieJie implements Girl {}
```

这时候类会直接报错，所以我们需要把这个类写的完全点。

```typescript
class xiaojiejie implements Girl2 {
    name: "大脚";
    age: 18;
    bust: 94;
    waistline: 21;
    sex: "女";
    say() {
      return "欢迎光临 ，红浪漫洗浴！！";
    };
};
```

## 9.4 接口的继承

接口也可以用于继承的，比如你新写一个`Teacher`接口，继承于`Person`接口。

```typescript
interface Teacher extends Girl2{
    teach(): string;
}
```

比如这时候，只看` Teacher `级别的简历，那我们需要修改`getResume()`方法。

```typescript
const getResume2 = (girl2: Teacher) => {
    console.log(girl2.name + "年龄是：" + girl2.age);
    console.log(girl2.name + "胸围是：" + girl2.bust);
    girl2.waistline && console.log(girl2.name + "腰围是：" + girl2.waistline);
    girl2.sex && console.log(girl2.name + "性别是：" + girl2.sex);
};
getResume2(girl2);
```

修改后，你就会发现下面我们调用`getResume2()`方法的地方报错了,因为这时候传的值必须有`Teach`方法，修改`girl`对象，增加`teach（）`方法，这时候就不会报错了。

```typescript
const girl2 = {
  name: "Wibus",
  age: 14,
  bust: 94,
  waistline: 21,
  sex: "女",
  say() {
    return "欢迎光临 ，红浪漫洗浴！！";
  },
    teach() {
    return "我是一个老师";
  },
};
```

关于接口的知识就讲到这里吧，这基本包含了接口 80%的知识

# Demo9.ts

```typescript
/**
 * Demo9.ts
 * TypeScript 的 interface 接口 2
 * @date 2021-1-2
 * @author Wibus
 */

 // 1 允许加入任意值
//  简历一般是有自由发挥的空间的，所以这时候需要一些任意值，就是自己愿意写什么就写什么。这时候interface接口也是支持的。
interface Girl1 {
    name: string;
    age: number;
    bust: number;
    waistline?: number;
    [name: string]: any; //属性的名字是字符串类型，属性的值可以是任何类型。
  }
// 这时候我们在对象里给一个性别
const girl = {
    name: "大脚",
    age: 18,
    bust: 94,
    waistline: 21,
    sex: "女",
  };
//   再修改一下代码，就没有错误了。
const getResume = (girl: Girl1) => {
    console.log(girl.name + "年龄是：" + girl.age);
    console.log(girl.name + "胸围是：" + girl.bust);
    girl.waistline && console.log(girl.name + "腰围是：" + girl.waistline);
    girl.sex && console.log(girl.name + "性别是：" + girl.sex);
  };
// 这时候我们的程序是不报错的，但是如果我们去掉刚才的设置，就会报错。

// 2 接口里的方法
// 接口里不仅可以存属性，还可以存方法，比如这时候有个say()方法，返回值是string类型。这时候你就不要再想成简历了，你需要更面向对象化的编程，想象成一个人。

interface Girl2 {
    name: string;
    age: number;
    bust: number;
    waistline?: number;
    [propname: string]: any;
    say(): string;
  }
// 加上这个say()方法后，程序马上就会报错，因为我们对象里没有 say 方法。那我们就要给对象一个 say 方法

const girl2 = {
  name: "Wibus",
  age: 14,
  bust: 94,
  waistline: 21,
  sex: "女",
  say() {
    return "欢迎光临 ，红浪漫洗浴！！";
  },
    teach() {
    return "我是一个老师";
  },
};

// 3 接口和类的约束
// 类和接口能有很好的结合

class xiaojiejie implements Girl2 {
    name: "大脚";
    age: 18;
    bust: 94;
    waistline: 21;
    sex: "女";
    say() {
      return "欢迎光临 ，红浪漫洗浴！！";
    };
};

// 4 接口的继承
// 接口也可以用于继承的，比如你新写一个Teacher接口，继承于Person接口。

interface Teacher extends Girl2{
    teach(): string;
}

// 比如这时候，只看 Teacher 级别的简历，那我们需要修改getResume()方法。
const getResume2 = (girl2: Teacher) => {
    console.log(girl2.name + "年龄是：" + girl2.age);
    console.log(girl2.name + "胸围是：" + girl2.bust);
    girl2.waistline && console.log(girl2.name + "腰围是：" + girl2.waistline);
    girl2.sex && console.log(girl2.name + "性别是：" + girl2.sex);
  };
  
getResume2(girl2);

```