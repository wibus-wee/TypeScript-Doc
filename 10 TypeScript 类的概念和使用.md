# 10 TypeScript 类的概念和使用

`TypeScript` 中类的概念和` ES6 `中原生类的概念大部分相同，但是也额外增加了一些新的特性。我在这里会完全从一个新手的角度，讲解类的各项知识点。

## 10.1 类的基本使用

新建一个文件，叫做`demo10.ts`,然后定义一个最简单的`Lady`类,这里要使用关键字`class`,类里边有姓名属性和一个得到姓名的方法
```typescript
class Lady {
    content = "Hi，帅哥";
    sayHello() {
      return this.content;
    }
}
  
const goddess = new Lady();
console.log(goddess.sayHello());
// ts-node demo10.ts
//result：Hi，帅哥
```

> 代码下面的注释的意思是：运行ts-node demo10.ts命令，得到的结果是：Hi，帅哥

这是一个最简单的类了，如果你有些编程经验，对这个一定很熟悉

## 10.2 类的继承

TypeScrip 的继承和ES6中的继承是一样的。关键字也是`extends`,比如我们这里新建一个`xiaoJieJie`的类，然后继承自`Lady`类，在`XiaoJieJie`类里写一个新的方法，叫做`sayLove`,具体代码如下。

```typescript
class xiaoJieJie extends Lady{
    sayLove(){
        return "I love you.";
    }
}

const Wibus = new xiaoJieJie();
console.log(Wibus.sayHello());
console.log(Wibus.sayLove());
// ts-node demo10.ts
// result: Hi，帅哥 I love you.
```
类写好以后，我们声明的对象是`xiaoJieJie`这个类，我们同时执行`sayHello()`和`sayLove()`都是可以执行到的，这说明继承起作用了

## 10.3 类的重写

讲了继承，那就必须继续讲讲重写，重写就是子类可以重新编写父类里边的代码。现在我们在`XiaoJieJies`这个类里重写父类的`sayHello()`方法

```typescript
class XiaoJieJies extends Lady {
    sayLove(){
        return "I love you.";
    }
    sayHello() {
        return "Hi, honey!";
      }
}

const wibus = new XiaoJieJies();
console.log(wibus.sayHello());
console.log(wibus.sayLove());
// ts-node demo10.ts
// result: Hi, honey! I love you.
```

## 10.4 super 关键字的使用

比如我们还是想使用`Lady`类中说的话，但是在后面，加上`你好`两个字就可以了。这时候就可以使用`super`关键字，它代表父类中的方法

```typescript
class Xiaojiejie extends Lady {
    sayLove() {
        return "I love you!";
      }
      sayHello() {
        return super.sayHello() + ".你好！";
      }
}

const goddesss = new Xiaojiejie();
console.log(goddesss.sayHello());
console.log(goddesss.sayLove());
// ts-node demo10.ts
// result: Hi，帅哥.你好！I love you!
```

那么整个下来呢，我们至少要知道TypoeScript中的类是如何定义和继承的。类中还有很多知识点要讲

## Demo10.ts

```typescript
/**
 * Demo10.ts
 * TypeScript 类的概念和使用
 * @date 2021-1-2
 * @author Wibus
 */

 // TypeScript 中类的概念和 ES6 中原生类的概念大部分相同，但是也额外增加了一些新的特性

// 1 类的基本使用
// 下面是最简单的类
class Lady {
    content = "Hi，帅哥";
    sayHello() {
      return this.content;
    }
}
  
const goddess = new Lady();
console.log(goddess.sayHello());
// ts-node demo10.ts
//result：Hi，帅哥

// 2 类的继承
// TypeScrip 的继承和ES6中的继承是一样的。关键字也是extends,比如我们这里新建一个XiaoJieJie的类，然后继承自Lady类，在XiaoJieJie类里写一个新的方法，叫做sayLove,具体代码如下。

class xiaoJieJie extends Lady{
    sayLove(){
        return "I love you.";
    }
}

const Wibus = new xiaoJieJie();
console.log(Wibus.sayHello());
console.log(Wibus.sayLove());
// ts-node demo10.ts
// result: Hi，帅哥 I love you.

// 类写好以后，我们声明的对象是XiaoJieJie这个类，我们同时执行sayHello()和sayLove()都是可以执行到的，这说明继承起作用了

// 3 类的重写
// 讲了继承，那就必须继续讲讲重写，重写就是子类可以重新编写父类里边的代码。现在我们在XiaoJieJie这个类里重写父类的sayHello()方法

class XiaoJieJies extends Lady {
    sayLove(){
        return "I love you.";
    }
    sayHello() {
        return "Hi, honey!";
      }
}

const wibus = new XiaoJieJies();
console.log(wibus.sayHello());
console.log(wibus.sayLove());
// ts-node demo10.ts
// result: Hi, honey! I love you.

// 4 super 关键字的使用
// 比如我们还是想使用Lady类中说的话，但是在后面，加上你好两个字就可以了。这时候就可以使用super关键字，它代表父类中的方法

class Xiaojiejie extends Lady {
    sayLove() {
        return "I love you!";
      }
      sayHello() {
        return super.sayHello() + ".你好！";
      }
}

const goddesss = new Xiaojiejie();
console.log(goddesss.sayHello());
console.log(goddesss.sayLove());
// ts-node demo10.ts
// result: Hi，帅哥.你好！I love you!

// 我们至少要知道TypoeScript中的类是如何定义和继承的。类中还有很多知识点要讲
```