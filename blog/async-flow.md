### Async Flow

> 请看示例代码

**片段 1**

```js
function getData(i) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(i)
    }, 2000)
  })
}

async function taskQueue() {
  for (let i = 0; i < 3; ) {
    const result = await getData(i)
    console.log(result)
    i++
  }
}
```

**片段 2**

```js
function getData(i) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(i)
    }, 2000)
  })
}
/**
 * 全部异步任务并行执行后返回
 */
async function taskQueue() {
  let arr = []
  for (let i = 0; i < 3; i++ ) {
    arr.push(getData(i))
  }
  return Promise.all(arr)
}
```

**片段 3**

```js
function getData(i) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(i)
    }, 2000)
  })
}
/**
 * 全部异步任务串行执行后返回
 */
async function taskQueue() {
  let arr = []
  for (let i = 0; i < 3; i++ ) {
    arr.push(await getData(i))
  }
  return arr
}
```