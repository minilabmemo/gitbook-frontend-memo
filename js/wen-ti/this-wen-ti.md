---
description: 問題
---

# this問題

```
const A={
    elem:5
}

const B={
    elem:10,
    getElem(num){
        return this.elem*num;
    }
}

const funA=B.getElem;
const funcBind=funA.bind(B);
console.log(B.getElem(10));
console.log(funA(10));
console.log(funcBind(10));
console.log(funA.call(A,10));
console.log(funA.call(B,10));
console.log(funA.apply(A,[10]));
console.log(funA.apply(B,[10]));
```





ans:

```
100
NaN
100
50
100
50
100
```
