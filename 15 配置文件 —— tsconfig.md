# 15 配置文件 —— tsconfig.json

应该有些人会看见一些ts项目里面都有一个`tsconfig.json`这个文件，那这里说下：这个是 TypeScript 的文件，虽然不常用，但是很重要。有必要详细的讲一下这个文件der～

## 15.1 生成tsconfig.json

这个文件是通过`tsc --init`命令生成的，在桌面上新建一个文件夹`TsDemo`,然后打开`VSCode`，把文件托到编辑器中，然后打开终端`Terminal`,输入`tsc --init`。

输入完成后，就会出现`tsconfig.json`文件，你可以打开简单的看一下，不过此时你可能看不懂。

其实它就是用来配置如何对`ts`文件进行编译的，我们都叫它 typescript 的编译配置文件。

> 如果此时你的`tsc`执行不了，很有可能是你没有全局安装 TypeScript,可以全局安装一下。
>
> 我在第一篇讲述过安装ts的：https://iucky.cn/posts/code/typescript-1

## 15.2 让 tsconfig.json 文件生效

你现在可以在文件夹跟目录建立一个`demo.ts`文件，然后编写一些最简单的代码，代码如下:

```typescript
const person: string = "wibus";
```

这时候我们不在使用`ts-node`直接执行了，需要用`tsc demo.ts`进行编译，编译后会得到`demo.js`文件。 生成的代码如下:

```typescript
var person = "wibus";
```

这时候好像一切都是正常的，但是我要告诉你的真相是`tsconfig.json`这个编译配置文件并没有生效。

此时我们打开`tsconfig.json`文件，找到`complilerOptions`属性下的`removeComments:true`选项，把注释去掉。

这个配置项的意思是，编译时不显示注释，也就是编译出来的`js`文件不显示注释内容。

现在你在文件中加入一些注释，比如：

```typescript
// I love wibus
const person: string = "wibus";
```

这时候再运行编译代码`tsc demo.ts`，编译后打开`demo.js`文件，你会发现注释依然存在，说明`tsconfig.json`文件没有起作用。

如果要想编译配置文件起作用，我们可以直接运行`tsc`命令，这时候`tsconfig.json`才起作用，可以看到生成的`js`文件已经不带注释了。

那现在又出现问题了，如果我们的跟目录下有多个`ts`文件，我们却只想编译其中的一个文件时，如何作？

我们在项目根目录，新建一个文件`demo2.ts`文件，然后也写一段最简单的 ts 代码。

```js
const person2: string = "jspang.com";
```

如果这时候我们在终端里运行`tsc`,虽然`tsconfig.json`生效了，但是两个文件都被我们编译了。这不是你想要的结果，我们可以用三种办法解决这个问题。

1. 第一种：使用 include 配置

`include`属性是用来指定要编译的文件的，比如现在我们只编译`demo.ts`文件，而不编译`demo2.ts`文件，就可以这样写。

写配置文件时有个坑需要注意，就是配置文件不支持单引号，所以里边都要使用双引号。

```js
{
  "include":["demo.ts"],
  "compilerOptions": {
      //any something
      //........
  }
}
```

这时候再编译，就只编译`demo.ts`文件了。

2. 第二种：使用 exclude 配置

`include`是包含的意思，`exclude`是不包含，除什么文件之外，意思是写再这个属性之外的而文件才进行编译。比如你还是要编译`demo.ts`文件，这时候的写法就应该是这样了。

```js
{
   "exclude":["demo2.ts"],
  "compilerOptions": {
      //any something
      //........
  }
}
```

这样写依然只有`demo.ts`被编译成了`js`文件。

3. 第三种：使用 files 配置

`files`的配置效果和`include`几乎一样，我是没找出有什么不同，只要配置到里边的文件都可以编译，如果有小伙伴知道有什么不同的，欢迎在视频下方留言，然后一起学习。

```js
{
  "files":["demo.ts"],
  "compilerOptions": {
      //any something
      //........
  }
}
```

结果是依然只有`demo.ts`文件被编译。这节课我们就学到这里，目的只是让大家初步了解一下`tsconfig.js`文件和它的使用方法，文件里边还有很多配置项，这些我们都会逐步讲到。