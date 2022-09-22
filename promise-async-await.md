# Promise/async/await

## [Callback function](https://developer.mozilla.org/en-US/docs/Glossary/Callback\_function)

* 含义：将 函数a 作为参数，传递给 函数b ，并且在函数b中调用函数a。那么 函数a 就是 函数b 的回调函数

```javascript
 示例：
 function cook(fn){
    setTimeout(()=>{
      console.log('先做饭');
      fn();
    },50000)
  }

  function eat(){
    console.log('再吃饭');
  }
  cook(eat);
```

* 使用场景：一般在封装函数时，并且需要异步操作的情况下
* **缺点**：回调地狱。会导致后期代码 可读性、维护性差
* **解决方案**：ES6 中的 Promise 一定程度上解决了回调地狱的问题（Promise不再用回调函数 封装异步代码，而是用Promise语法进行封装）

## [Promise](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/Promise)

* Promise的三种状态：pending、resolved、rejected
* 状态间转换 只能有**两种**情况（二选一）：
  * pending ---- resolved
  * pending ---- rejected

```javascript
示例：

let p = new Promise(function(resolve,reject){
    let n = 100;
    setTimeout(()=>{
      n++;
      if(n % 2 == 0){ 
        resolve(n); 
      }else{
        reject(n);
      }
    },3000)
  });

  p.then(function(res){
    console.log(res);     // resolved
  }).catch(function(result){
    console.log(result); }).finally() // rejected

状态间转换 只能有两种情况：

  let p = new Promise((resolve)=>{
    resolve(10);
  })

  p.then((res)=>{ 
    console.log(res); // 10
    res++;
    return new Promise((resolve)=>{
      resolve(res)
    })
  }).then((res2)=>{ 
    // pennding ---- resolve
    console.log(res2);  // 11
  })
```

## [Promise.all()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/Promise/all)

* 只要任何一个输入的 promise 的 reject 回调执行或者输入不合法的 promise 就会立即抛出错误，并且 reject 的是第一个抛出的错误信息。

```javascript
const promise1 = Promise.resolve(3);
const promise2 = 42;
const promise3 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, 'foo');
});

Promise.all([promise1, promise2, promise3]).then((values) => {
  console.log(values);
});
// expected output: Array [3, 42, "foo"]

```

## [async/await](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/async\_function)

* ES8 中 async/await 解决 回调地狱的 最佳方案
* 关键字 async：放在函数前面，表示这个函数为异步函数，而后 方可在函数内部使用await
* 关键字 await：在有async关键字 的函数中使用，await 写在 Promise 对象前面（把异步代码写得像同步代码的结构一样）

```javascript
示例：

  async function fn() {
    // 完成需求1
    let res1 = await pAjax({
      url: 'http://localhost:8888/test/aa'
    });
    console.log(res1);

    // 完成需求2
    let res2 = await pAjax({
      url: 'http://localhost:8888/test/bb',
      dataType: 'json'
    })
    console.log(res2);

    // 完成需求3
    let res3 = await pAjax({
      url: 'http://localhost:8888/test/cc',
      dataType: 'json',
      data: {
        name: 'potato',
        id: '1002'
      }
    })
    console.log(res3);
  }
  
  fn(); 
```

## [返回目录](./)
