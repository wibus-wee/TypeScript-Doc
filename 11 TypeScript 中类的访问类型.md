# 11 TypeScript 中类的访问类型

上节已经简单学习了`TypeScript`中类的使用，这节我们继续学习一下类中的访问类型。其实类的访问类型就是基于三个关键词`private`、`protected`和`public`,也是三种访问类型

## 11.1 简单的类

我们来写一个简单的类先，我们定义一个 Person 类，然后使用这个类的对象，进行赋值，最后打印在控制台上。

```typescript
class Person {
    name: string;
  }
  
const person = new Person();
person.name = "Wibus";
  
console.log(person.name);
// ts-node demo11.ts
// result: Wibus
```

写完后我们直接可以在`Terminal`(中),输入`ts-node demo11.ts`进行查看结果，结果会打印出`Wibus`

## 11.2 public 访问属性

这时候可以打出Wibus是因为我们如果不在类里对name的访问属性进行定义，那么它就会默认是public访问属性。所以，我们刚刚所写的类相当于这样子

```typescript
class Person2 {
    public name: string;
};
```

> `public`从英文字面的解释就是`公共的`或者说是`公众的`，在程序里的意思就是允许在类的`内部`和`外部`被调用.

比如说，我们在类里面写一个`sayHello()` 方法，访问属性为`public`

```typescript
class Person3 {
    public name: string;
    public sayhello(){
        console.log(this.name + ' say hello');
    };
};
// ————————下面的是外部调用——————————
const person3 = new Person3;
person3.name = "Wibus";
person3.sayhello();
// ts-node demo11.ts
// result: Wibus say hello
```

这是的`this.name`就是类的内部调用。我们在下面在执行一下这个方法`person3.sayHello()`, 终端中可以看到一切正常运行了，顺利打印

## 11.3 private 访问属性

> `private` 访问属性的意思是，只允许在类的内部被调用，外部不允许调用

现在我们把` name `属性改成`private`,这时候在类的内部使用不会提示错误，而`外部`,以及子类使用`VSCode`直接会报错。

```typescript
class Person4 {
    private name: string;
    private sayhello(){
        console.log(this.name + ' say hello');
    };
};

class Person_Person4 extends Person4 {
    public saySomeThing() {
        console.log(this.name); 
    }
}
//VSC Error: 属性“name”为私有属性，只能在类“Person4”中访问。
// ————————下面的是外部调用——————————
const person4 = new Person4;
person4.name = "Wibus";
person4.sayhello();
// VSC Error: 属性“sayhello”为私有属性，只能在类“Person4”中访问。
```

## 11.4 protected 访问属性

> `protected` 允许在类内及继承的子类中使用

把name的访问属性换成`protected`,这时候`外部`调用`name`的代码会报错，`内部`的不会报错，和`private`一样。这时候我们再写一个`Person_Person5`类，继承于`Person4`

```typescript
class Person5 {
    protected name: string;
    protected sayhello(){
        console.log(this.name + ' say hello');
    };
};

class Person_Person5 extends Person5 {
    public sayBye(){
        return "this.name";
    }
}

// ————————外部调用——————————
const person5 = new Person5;
person5.name = "Wibus";
person5.sayhello();
// VSC Error: 属性“sayhello”受保护，只能在类“Person5”及其子类中访问。
// ————————Person_Person5 类 ——————
const person_person5 = new Person_Person5;
person_person5.sayBye(); //VSC 不报错
```

那么通过这个例子相信你一定知道什么是类的内部和类的外部，也知道了三个访问类型的区别了

## Demo11.ts

```typescript
/**
 * Demo11.ts
 * TypeScript 中类的访问类型
 * @date 2021-1-3
 * @author Wibus
 */

// 上节已经简单学习了TypeScript中类的使用，这节我们继续学习一下类中的访问类型。其实类的访问类型就是基于三个关键词private、protected和public,也是三种访问类型

// 1 简单的类

class Person {
    name: string;
  }
  
const person = new Person();
person.name = "Wibus";
  
console.log(person.name);
// ts-node demo11.ts
// result: Wibus

// 2 public 访问属性
// 这时候可以打出Wibus是因为我们如果不在类里对name的访问属性进行定义，那么它就会默认是public访问属性。

// 相当于
class Person2 {
    public name: string;
};
// public从英文字面的解释就是公共的或者说是公众的，在程序里的意思就是允许在类的内部和外部被调用.
class Person3 {
    public name: string;
    public sayhello(){
        console.log(this.name + ' say hello');
    };
};
// ————————下面的是外部调用——————————
const person3 = new Person3;
person3.name = "Wibus";
person3.sayhello();
// ts-node demo11.ts
// result: Wibus say hello

// 3 private 访问属性
// private 访问属性的意思是，只允许在类的内部被调用，外部不允许调用

class Person4 {
    private name: string;
    private sayhello(){
        console.log(this.name + ' say hello');
    };
};

class Person_Person4 extends Person4 {
    public saySomeThing() {
        console.log(this.name); 
    }
}
//VSC Error: 属性“name”为私有属性，只能在类“Person4”中访问。
// ————————下面的是外部调用——————————
const person4 = new Person4;
person4.name = "Wibus";
person4.sayhello();
// VSC Error: 属性“sayhello”为私有属性，只能在类“Person4”中访问。


// 4 protected 访问属性
// protected 允许在类内及继承的子类中使用

class Person5 {
    protected name: string;
    protected sayhello(){
        console.log(this.name + ' say hello');
    };
};

class Person_Person5 extends Person5 {
    public sayBye(){
        return "this.name";
    }
}

// ————————外部调用——————————
const person5 = new Person5;
person5.name = "Wibus";
person5.sayhello();
// VSC Error: 属性“sayhello”受保护，只能在类“Person5”及其子类中访问。
// ————————Person_Person5 类 ——————
const person_person5 = new Person_Person5;
person_person5.sayBye(); //VSC 不报错
```