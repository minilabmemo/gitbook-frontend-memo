# pass by?

```

const P= function(f,s){
    this.f=f;
    this.s=s;
}

P.prototype.setF=function(newF){
    this.f=newF;
    return this;
    
}

const arr=[];

arr[0]=new P('f','s');
arr[1]=arr[0].setF('s');

console.log(arr);//?
console.log(arr[0]===arr[1]);//?


//ans
[ P { f: 's', s: 's' }, P { f: 's', s: 's' } ]
true

```
