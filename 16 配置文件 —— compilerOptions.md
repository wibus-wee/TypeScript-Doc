# 16 配置文件 —— compilerOptions

`compilerOptions`配置项，它是告诉`TypeScript`具体如何编译成`js`文件的，里边的配置项非常多，我们先来看看几个简单的配置项，目的是让你熟悉`compilerOptions`的使用方法。

## 16.1 removeComments 属性

`removeComments`是`complerOptions`里的一个子属性，它的用处是告诉`TypeScript`对编译出来的`js`文件是否显示注释（注解）。比如我们现在把`removeComments`的值设置为`true`，就是在`js`中不显示注释。

我们把上节课文件没有的`Demo2.ts`和生成的 JS 文件都删除掉，只留`Demo.ts`文件，然后再`Demo.ts`文件里，加入一个注释。

```typescript
// I‘m Wibus
const person: string = "Wibus";
```

写完注释后，直接再终端`Terminal`里，输入`tsc`,输入完成后，很快就会生成一个`demo.js`文件，打开后会看到下面的代码。

```typescript
"use strict";
var person = "Wibus";
```

你写的注释并没有编译到`demo.js`里。如果我们反之，把`removeComments`的值，设置为`false`,这时候`demo.js`里就会有注释内容了。

```typescript
"use strict";
// I‘m Wibus
var person = "Wibus";
```

## 16.2 strict 属性

`strict`属性如果设置为`true`,就代表我们的编译和书写规范，要按照`TypeScript`最严格的规范来写，如果我们把这个设置为`false`或者注释掉，意思是我们可以对设置一些不严格的写法。

## 16.3 noImplicitAny 属性

`noImplicitAny`属性的作用是，允许你的注解类型 any 不用特意表明，只听概念很难理解。这就是看我视频的一个好处，如果你只看官方 API，你可能要迷糊一阵啥叫`允许你的注解类型any不用特意表明`,这就是每个汉字我都认识，连在一期就不知道啥意思的最好诠释。

为了更好的说明，我们举个例子,在`demo.ts`里，删除刚才的代码，然后写一个方法，方法的参数我们设置成任意类型(any)。

```typescript
function Wibus(name) {
  return name;
}
```

这时候我们的`TypeScript`是进行报错的，我们用`tsc`编译也是报错的。这就是因为我们开启了`strict:true`,我们先注释掉，然后把`noImplicitAny`的值设置为`false`,就不再报错了。

如果设置为`noImplicitAny:true`,意思就是值就算是 any（任意值），你也要进行类型注释。

```typescript
function Wibus(name: any) {
  return name;
}
```

你可以简单的理解为，设置为 true，就是必须明确置顶 any 类型的值。

## 16.4 strictNullChecks 属性

我们先把`strictNullChecks`设置为`false`,它的意思就是，**不强制检查 NULL 类型。**我们举个例子，让你能一下子就明白，还是删除`demo.ts`里的代码，然后编写代码.

```typescript
const Wibus: string = null;
```

代码写完后，你会发现这段代码是不报错的，如果是以前，一定是报错的，这就是我们配置了“不强制检验 null 类型”。如果你设成`strictNullChecks:true`，这时候就报错了。

## 16.5 ts-node 的遵循

`tsc fileName` 是没办法遵循`tsconfig.js`文件的，那`ts-node`是否遵循?

这里直接告诉你答案，`ts-node`是遵循的，感兴趣的可以自行试一下。

这节课我们就是简单的认识一下`compilerOptions`属性的配置，其实这些你只要掌握方法，并不需要记忆，我也是记不住每一项是干嘛的，用的时候会查 API 就可以了。Next，我们继续学习配置文件