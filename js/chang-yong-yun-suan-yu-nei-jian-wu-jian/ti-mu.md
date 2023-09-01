---
description: 題目
---

# 題目

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


console.log(x['bar'].f)//這樣也可以，看來是因為物件key是字串
//console.log(x['bar'].'f')//SyntaxError: Unexpected string
console.log(x['bar']['f'])

//我知道const不能改，但如果是改陣列裡面的值呢
const bar=[10,10,10];
bar[2]=100
console.log(bar)
//foreach用法 重點？

//bind apply用法

//throw catch

```
