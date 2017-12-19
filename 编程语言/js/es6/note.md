# note

## let 
块级作用域
```js
for(let i=0;i<10;i++){
  let i=10;
  console.log(i);
}
```

## 变量结构赋值
```js
let [a,b]=[1,2]
let [a=0,b=0]=[]

function a({x,y=1}){
}
a({x:1,y:2})
a({x:1})
```

## 拓展运算符
...
```js
Math.max(...[1,2,3])
//Math.max(1,2,3)

//复制数组
const a1=[1,2,3]
const a2=[...a1]

[...a1,...a2]

[...'hello']
function length(str) {
  return [...str].length;
}
```

## promise

## generator 和 yield 关键字 


[es6入门](http://es6.ruanyifeng.com/)
