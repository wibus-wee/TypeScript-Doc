# 1 Typescript环境搭建

如果你想使用 TypeScript 来编写代码，你需要先安装一下它的开发环境，这并不复杂。

1.安装 `Node` 的运行环境

你可以到`Node.js`官网去下载 Node 进行安装( https://node.js.org )，建议你下载LTS版本,也就是长期支持版本。安装的过程我就不演示了，这个过程就和安装 QQ 一样，没有任何难度。

如果你已经安装了，可以打开命令行工具，然后使用node -v命令查看安装的版本，但是一般还有一个命令需要检测一下，就是npm -v,如果两个命令都可以输出版本号，说明你的 Node 安装已经没有任何问题了。

2.`全局安装` typeScript

你要使用 TypeScript 先要在你的系统中全局安装一下TypeScript，这里你可以直接在 VSCode 中进行安装，安装命令可以使用` npm` 也可以使用 `yarn`

```sh
npm install typescript -g
yarn global add typescript
```

这两个你使用那个都是可以的，根据喜好自行选择，我使用的npm进行安装。

我们在一个目录下新建`Demo1.ts`,输入下面的代码：

```typescript
function hello() {
  let web: string = "Hello World";
  console.log(web);
}

hello();
```

使用node Demo1.ts时，会出现报错。所以我们需要先tsc Demo.ts，在目录下将会生成Demo1.js，我们再node Demo1.js就没事了

## 1.1 ts-node 工具

但是这样操作的效率实在是太低了，你可以使用ts-node插件来解决这个问题，有了这个插件，我们就不用再编译了，而使用ts-node就可以直接看到编写结果。

使用`npm`命令来全局安装，直接在命令行输入下面的命令：

```bash
npm install -g ts-node
```

安装完成后，就可以在命令中直接输入如下命令，来查看结果了。

```bash
ts-node Demo1.ts
```

## Demo1.ts

```typescript
function hello() {
  let web: string = "Hello World";
  console.log(web);
}

hello();
```
