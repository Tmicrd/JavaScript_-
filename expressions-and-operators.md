# Expressions & operators

## [Conditional (ternary) operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional\_Operator)

```javascript
const score = 90;
let result;

// 用 if else
if (score >= 60) {
  result = "pass"
} else {
  result = "fail"
}

// 用ternary operator 代替 if else
const result1 = score >= 60 ? "pass" : "fail"
const result2 = score >= 60 ? (score >= 80 ? "excellent" : "pass") : "fail"

console.log(result1, result2) // pass excellent
```

## [Optional chaining (?.)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional\_chaining)

<pre class="language-javascript" data-title="短路 返回 undefined"><code class="lang-javascript">const order ={
  name: 1007,
  isDone: true
}

// 早期方法 &#x26;&#x26; 判断 ？之前的值 是否存在
// const r1 = order.name &#x26;&#x26; order.name.toString()  // 1007
// const r2 = order.id &#x26;&#x26; order.id.toString()      // order.id 不存在，所以 &#x26;&#x26; 之后的代码不会执行
<strong>
</strong><strong>// 现在用 ?. 更简便
</strong><strong>const r3 = order?.name &#x26;&#x26; order?.id?.toString()    // undefined
</strong>const r4 = order?.orderName?.toString()            // undefined</code></pre>

## [Nullish coalescing operator (??)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish\_coalescing\_operator)

<pre class="language-javascript"><code class="lang-javascript"><strong>// ||  如果true 返回左侧(默认转为布尔值 再判断)，否则返回右侧
</strong>// ??  如果true 返回左侧，否则返回右侧。有且只有 两种情况为false：null 和 undefined

// ||  得不到特殊值： 0， ''， NaN，"false"

console.log(undefined || 'default' ) // default
console.log(null || 'default')       // default
console.log(false || 'default')      // default
console.log(0 || 'default')          // default
console.log(NaN || 'default')        // default
console.log("" || 'default')         // default

console.log(undefined ?? 'default')  // 'default'
console.log(null ?? 'default')       // 'default'
console.log(false ?? 'default')      // 'false'
console.log(0 ?? 'default')          // 0
console.log(NaN ?? 'default')        // NaN
console.log("" ?? 'default')         // 

// 赋值时，可以简写 ??=
const city = {weather: "sunny", name: null}
city.weather ??= 20
city.name ??= "ChongQing"     // { weather: 'sunny', name: 'ChongQing' }</code></pre>

## [Bitwise NOT (\~)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise\_NOT)

```javascript
// 正数同 Math.floor()，负数同 Math.ceil()
~~1.7                // 1 
Math.floor(1.7)      // 1
 
~~-1.3               // -1
Math.ceil(-1.3)      // -1
```

## [Logical AND (&&)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical\_AND)  [Logical OR (||)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical\_OR)

```javascript
//  || 左侧为真，返回左侧，否则返回右侧
//  && 左侧为真，返回右侧，否则返回左侧
const h = null && 10               // null
const i = 0 && 10                  // 0
const j = NaN && 10                // NaN
const k = undefined && 10          // undefined

const w = null || "hi"             // hi
const x = 0 || "hi"                // hi
const y = NaN || "hi"              // hi
const z = undefined || "hi"        // hi
```

## [返回目录](./)
