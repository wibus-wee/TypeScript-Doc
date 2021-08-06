# 19 Enum 枚举类型

这节主要学一下 TypeScript 中枚举(`enum`)类型的使用，你如果在程序中能灵活的使用枚举(`enum`),会让程序有更好的可读性。这里我拿每次去“大宝剑”点餐作个比喻。

## 一场大保健

比如说我要去做个大保健，那么我需要通过🎲来随机选择一项服务，下面是三个例子，分别看看那个才是高级的写法

```typescript
function getServe(status: number) {
  if (status === 0) {
    return "massage";
  } else if (status === 1) {
    return "SPA";
  } else if (status === 2) {
    return "dabaojian";
  }
}
const result = getServe(0);
console.log(`我要去${result}`);
```

```typescript
const Status = {
  MASSAGE: 0,
  SPA: 1,
  DABAOJIAN: 2,
};

function getServe(status: any) {
  if (status === Status.MASSAGE) {
    return "massage";
  } else if (status === Status.SPA) {
    return "spa";
  } else if (status === Status.DABAOJIAN) {
    return "dabaojian";
  }
}

const result = getServe(Status.SPA);

console.log(`我要去${result}`);
```

```typescript
enum Status {
  MASSAGE,
  SPA,
  DABAOJIAN,
}

function getServe(status: any) {
  if (status === Status.MASSAGE) {
    return "massage";
  } else if (status === Status.SPA) {
    return "spa";
  } else if (status === Status.DABAOJIAN) {
    return "dabaojian";
  }
}

const result = getServe(Status.SPA);

console.log(`我要去${result}`);
```

那么当然就是最后一个了，请出主角`enum`

## 枚举类型的对应值

我们正常人的思路来看的话，你调用时传一个`1`,并不会输出`我要去spa`，然鹅

```typescript
const result = getServe(1);
// 我要去spa
```

这看起来很神奇，这是因为枚举类型是有对应的数字值的，默认是从 0 开始的。我们直接用`console.log()`就可以看出来了，这和C语言的数组排序有点类似，C语言的数组也是从0开始数的（其实好多都是啦）

```typescript
console.log(Status.MASSAGE);
console.log(Status.SPA);
console.log(Status.DABAOJIAN);
```

可以看出结果就是`0,1,2`。那这时候不想默认从 0 开始，而是想从 1 开始。可以这样写。

```typescript
enum Status {
  MASSAGE = 1,
  SPA,
  DABAOJIAN,
}
```

## 枚举通过下标反查

我们这里能打印出枚举的值(也有叫下标的)，那如果我们知道下标后，也可以通过反差的方法，得到枚举的值。

```typescript
console.log(Status.MASSAGE, Status[1]);
```

这样就进行了反查。