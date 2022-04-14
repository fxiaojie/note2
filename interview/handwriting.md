## 数组扁平化

```js
function flatten(arr) {
	return arr.reduce((result, item) => {
		return result.concat(Array.isArray(item) ? flatten(item) : item);
  }, []);
}
```

## 深拷贝

```js
function cloneDeep (target) {
  // 判断是否传入类型为Object
  if(typeof target !== 'object' || !target) {
    return target;
  }
  // 声明新对象
  let newTarget = target instanceof Array === true ? [] : {};
  // 循环对象 递归复制给新对象
  for(let key in target) {
    // 判断属性是否在对象本身上
    if(target.hasOwnProperty(key)) {
      // 递归调用
      newTarget[key] = cloneDeep(target[key]);
    }
  }
  // 返回新对象
  return newTarget;
}
```

## 浅拷贝

```js
Object.assign(target,source)
```

## 防抖

```js
function debounce(fn, delay, immediate = false) {
  // 1.定义一个定时器, 保存上一次的定时器
  let timer = null
  let isInvoke = false

  // 2.真正执行的函数
  const _debounce = function(...args) {
    // 取消上一次的定时器
    if (timer) clearTimeout(timer)

    // 判断是否需要立即执行
    if (immediate && !isInvoke) {
      fn.apply(this, args)
      isInvoke = true
    } else {
      // 延迟执行
      timer = setTimeout(() => {
        // 外部传入的真正要执行的函数
        fn.apply(this, args)
        isInvoke = false
      }, delay)
    }
  }

  return _debounce
}
```

## 节流

```js
function throttle(fn, interval) {
  // 1.记录上一次的开始时间
  let lastTime = 0

  // 2.事件触发时, 真正执行的函数
  const _throttle = function() {

    // 2.1.获取当前事件触发时的时间
    const nowTime = new Date().getTime()

    // 2.2.使用当前触发的时间和之前的时间间隔以及上一次开始的时间, 计算出还剩余多长事件需要去触发函数
    const remainTime = interval - (nowTime - lastTime)
    if (remainTime <= 0) {
      // 2.3.真正触发函数
      fn()
      // 2.4.保留上次触发的时间
      lastTime = nowTime
    }
  }

  return _throttle
}
```

## call

```js
Function.prototype.hycall = function(thisArg, ...args) {
  // 1.获取需要被执行的函数
  const fn = this

  // 2.对thisArg转成对象类型(防止它传入的是非对象类型)
  thisArg = (thisArg !== null && thisArg !== undefined) ? Object(thisArg): window

  // 3.调用需要被执行的函数
  thisArg.fn = fn
  const result = thisArg.fn(...args)
  delete thisArg.fn

  // 4.将最终的结果返回出去
  return result
}
```

## apply

```js
Function.prototype.hyapply = function(thisArg, argArray) {
  // 1.获取到要执行的函数
  const fn = this

  // 2.处理绑定的thisArg
  thisArg = (thisArg !== null && thisArg !== undefined) ? Object(thisArg): window

  // 3.执行函数
  thisArg.fn = fn

  argArray = argArray || []
  const result = thisArg.fn(...argArray)

  delete thisArg.fn

  // 4.返回结果
  return result
}
```

## bind

```js
Function.prototype.hybind = function(thisArg, ...argArray) {
  // 1.获取到真实需要调用的函数
  const fn = this

  // 2.绑定this
  thisArg = (thisArg !== null && thisArg !== undefined) ? Object(thisArg): window

  function proxyFn(...args) {
    // 3.将函数放到thisArg中进行调用
    thisArg.fn = fn
    // 特殊: 对两个传入的参数进行合并
    const finalArgs = [...argArray, ...args]
    const result = thisArg.fn(...finalArgs)
    delete thisArg.fn

    // 4.返回结果
    return result
  }

  return proxyFn
}
```

## promise

```js

```

## 数组去重

```js
[...new Set(arr)]
```

## 函数柯里化

```js
function hyCurrying(fn) {
  function curried(...args) {
    // 判断当前已经接收的参数的个数, 可以参数本身需要接受的参数是否已经一致了
    // 1.当已经传入的参数 大于等于 需要的参数时, 就执行函数
    if (args.length >= fn.length) {
      // fn(...args)
      // fn.call(this, ...args)
      return fn.apply(this, args)
    } else {
      // 没有达到个数时, 需要返回一个新的函数, 继续来接收的参数
      function curried2(...args2) {
        // 接收到参数后, 需要递归调用curried来检查函数的个数是否达到
        return curried.apply(this, args.concat(args2))
      }
      return curried2
    }
  }
  return curried
}
```

