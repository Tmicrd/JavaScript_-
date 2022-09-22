# reduce()

<pre class="language-javascript"><code class="lang-javascript"><strong>// 基本用法
</strong><strong>
</strong><strong>const arr1 = [1, 2, 3]
</strong>const arr2 = [{ x: 1 }, { x: 2 }, { x: 3 }]
const arr3 = [[1,2],[3,4],[5,6],[7,8]]

// 求arr1中 数字的和为：6
const res1 = arr1.reduce((pre, cur, index) => {
  return pre + cur
},
  0)

// 初始值为10，求10 与arr2 中所有x的值的和为：16
const res2 = arr2.reduce((pre, cur, index) => {
  return pre + cur.x
},
  10)

// 初始值 {x: 0}, 返回值 {x: 6}
const res3 = arr2.reduce((pre, cur, index) => {
  return { x: pre.x + cur.x }
},
  { x: 0 })

// 初始值为 [], 返回值 [1, 2, 3, 4, 5, 6, 7, 8]
<strong>const res = arr3.reduce((pre, cur,index) => {
</strong>  pre.push(...cur)
  return pre
}, [])
</code></pre>

```javascript
// Flap

const arr = [[1, 2], [3, 4], [5, 6]]
// 要得到结果： flap: [ 1, 2, 3, 4, 5, 6 ]

方法一：
const flap = arr.reduce((pre,cur)=>{
  return [...pre, ...cur]
},[])

方法二：
const flap = arr.reduce((pre,cur)=>{
  console.log("pre:", pre, "cur:", cur)
  pre.push(...cur)
  return pre
},[])
```

```javascript
// 案例

const Queue = [ 
  'Q1-N1',
  'Q1-N2',
  'Q2-N1',
  'Q2-N2',
]

const result = Queue.reduce(
  (pre, cur) => {
    if(cur.split("-")[0] === "Q1") {
      pre["Q1"].push({key:cur,label:cur})
    }

    if(cur.split("-")[0] === "Q2") {
      pre["Q2"].push({key:cur,label:cur})
    }
    
    return pre
  },
  // 初始值设为一个 Object， Key 分别为Q1、Q2，value 都为空array
  {Q1: [], Q2: []}
)
// 返回值 是一个包含 Q1、Q2的 Object

//{
//   Q1: [
//     { key: 'Q1-N1', label: 'Q1-N1' },
//     { key: 'Q1-N2', label: 'Q1-N2' },
//   ],
//   Q2: [
//     { key: 'Q2-N1', label: 'Q2-N1' },
//     { key: 'Q2-N2', label: 'Q2-N2' },
//   ]
// }


// 简化后
const result = Queue.reduce(
  (pre, cur) => {
    cur.split("-")[0] === "Q1" ？pre["Q1"].push({key:cur,label:cur})
    : pre["Q2"].push({key:cur,label:cur})
    
    return pre
  },
  {Q1: [], Q2: []}
)
```

## [返回目录](./)
