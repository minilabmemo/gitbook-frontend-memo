---
description: 問題
---

# 問題



```
//嘗試印一個不存在index的陣列會？
const arr=[100];
console.log(arr[1])//?
console.log(arr[0]+arr[1])//?
console.log(2+[])//?
console.log(2+ +'1')//?

//嘗試印一個不存在物件的索引會？
const x={};
x['foo']='bar';
x.bar={
    'f':123,
}

console.log(x)
console.log(x['bar'].f)//這樣也可以，看來是因為物件key是字串
//console.log(x['bar'].'f')//SyntaxError: Unexpected string
console.log(x['bar']['f'])

//我知道const不能改，但如果是改陣列裡面的值呢
const bar=[10,10,10];
//bar=[10,10,10];//TypeError: Assignment to constant variable.
bar[2]=100
console.log(bar)//竟然可以[ 10, 10, 100 ]


//丟進function竟然也可以
function changeArr(arr){
    arr[1]=150;
}
const arr100=[100];
changeArr(arr100)
console.log(arr100[0]+arr100[1])//竟然可以250

//如果沒有給足參數會是？
function foo(x,y){
    console.log(x+","+y)
}
console.log(foo("!!"))//是!!,undefined

//錯誤的類型函式引用
let a=5;
console.log(a.substring(0,3))//TypeError: a.substring is not a function
//String 的substring() 方法返回该字符串从起始索引到结束索引（不包括）

```



