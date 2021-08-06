# 22 初识命名空间——Namespace

## 没有命名空间的时候

我们先用类来实现 header, content, footer，类似于template，就像这样：

```typescript
class Header {
  constructor() {
    const elem = document.createElement("div");
    elem.innerText = "This is Header";
    document.body.appendChild(elem);
  }
}

class Content {
  constructor() {
    const elem = document.createElement("div");
    elem.innerText = "This is Content";
    document.body.appendChild(elem);
  }
}

class Footer {
  constructor() {
    const elem = document.createElement("div");
    elem.innerText = "This is Footer";
    document.body.appendChild(elem);
  }
}

class Page {
  constructor() {
    new Header();
    new Content();
    new Footer();
  }
}
```



接着使用 `tsc` 来进行编译，接着放上web来运行一下

虽然虽然这段代码没有任何问题，但是有的人会发现这暴露了过多的全局变量，变得在之后维护会显得一发不可收拾。最好的是，只需要有`Page`这个全局变量即可，其他的可以不暴露到全局

## 使用命名空间

命名空间有个关键词：`namespace`，比如说`namespace Home`，需要变成全局的类使用`export`暴露，那么代码将会变成这样：

```typescript
namespace Home{
  class Header {
    constructor() {
      const elem = document.createElement("div");
      elem.innerText = "This is Header";
      document.body.appendChild(elem);
    }
  }

  class Content {
    constructor() {
      const elem = document.createElement("div");
      elem.innerText = "This is Content";
      document.body.appendChild(elem);
    }
  }

  class Footer {
    constructor() {
      const elem = document.createElement("div");
      elem.innerText = "This is Footer";
      document.body.appendChild(elem);
    }
  }

  export class Page {
    constructor() {
      new Header();
      new Content();
      new Footer();
    }
  }
}
```

这个时候只会有Home.Page是全局的了

