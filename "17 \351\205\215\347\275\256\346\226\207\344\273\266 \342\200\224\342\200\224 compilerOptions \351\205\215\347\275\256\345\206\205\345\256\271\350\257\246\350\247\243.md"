# 17 配置文件 —— compilerOptions 配置内容详解

我们继续讲`complierOptions`里的配置项，里边的内容很多，我只能选几个重要的给大家讲讲，然后在这节最后，我会给出大家自己查询的方法。需要再次说明的是，这些配置项没必要记，因为他们真的不是每天都需要用到，所以你只要知道如何配置和重要的几项，学会在自己需要时如何查询就可以了。

## rootDir 和 outDir

现在你的`js`文件直接编译到了根目录下，和`ts`文件混在了一起。我们当然是不喜欢这种方法的，工作中我们希望打包的`js`都生成在特定的一个文件夹里,比如`build`。

这时候你就可以通过配置`outDir`来配置，当然你也可以通过`rootDir`来指定`ts`文件的位置，比如我们把所有的 ts 文件都放到 src 下。那配置文件就应该这样写。

```js
{
    "outDir": "./build" ,
    "rootDir": "./src" ,
}
```

这时候你再在`Terminal`中输入`tsc`,就会有不同的效果了。

## 编译 ES6 语法到 ES5 语法-allowJs

现在你在`src`目录下用`ES6`的语法写了一个`demo2.js`文件，代码如下。

```js
export const name = "wibus";
```

如果你不做任何配置，这时候试用`tsc`是没有效果的。你需要到`tsconfig.js`文件里进行修改，修改的地方有两个。

```js
"target":'es5' ,  // 这一项默认是开启的，你必须要保证它的开启，才能转换成功
"allowJs":true,   // 这个配置项的意思是联通
```

这两项都开启后，在使用`tsc`编译时，就会编译`js`文件了。

## sourceMap 属性

如果把`sourceMap`的注释去掉，在打包的过程中就会给我们生成`sourceMap`文件.

> sourceMap 简单说，Source map 就是一个信息文件，里面储存着位置信息。也就是说，转换后的代码的每一个位置，所对应的转换前的位置。有了它，出错的时候，除错工具将直接显示原始代码，而不是转换后的代码。这无疑给开发者带来了很大方便。

这里我不对 Source map 文件详细讲解，如果你感兴趣，可以自行百度一下吧。

## noUnusedLocals 和 noUnusedParameters

比如现在我们修改`demo.ts`文件的代码，改为下面的样子。

```js
const wibus: string = null;
export const name = "wibus";
```

这时候你会发现`wibus`这个变量没有任何地方使用，但是我们编译的话，它依然会被编译出来，这就是一种资源的浪费。

```js
//编译后的文件
"use strict";
exports.__esModule = true;
exports.name = void 0;
var wibus = null;
exports.name = "wibus";
```

这时候我们可以开启`noUnusedLocals：true`，开启后我们的程序会直接给我们提示不能这样编写代码，有没有使用的变量。

`noUnusedParameters`是针对于名优使用的函数的，方法和`noUnusedLocals：true`一样，小伙伴们自己尝试吧。

我们讲了几个最常用的方法，如果你需要全面的了解，可以查看这个网址：

> https://www.tslang.cn/docs/handbook/compiler-options.html (编译选项详解)

自己进行查看就可以了。

好了配置文件我们就暂时告一段落了，下节课我们讲一下 TypeScript 里的联合类型。