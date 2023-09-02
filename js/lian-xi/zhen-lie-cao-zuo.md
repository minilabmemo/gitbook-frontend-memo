---
description: 陣列操作
---

# 陣列操作

```javascript
//宣告空間後再加入會怎樣
const arr2=new Array(1);
console.log(arr2);//[ <1 empty item> ]
arr2.length=2;
console.log(arr2);//[ <2 empty items> ]
arr2.push(2);
arr2.push(0);
console.log(arr2);//[ <2 empty items>, 2, 0 ]

//for in 代表遍巡key, 會跳過空值
for(const num in arr2){
  console.log(num);
}
```



### sort

* 如果 compareFunction 沒有被應用,預設的排序順序是根據"<mark style="background-color:red;">被轉換成字串的 Unicode</mark>" 編碼位置（code points）而定
* 排序後的陣列。請注意此為原地（in place）進行排序過的陣列，並且不是原陣列的拷貝。

```javascript
//預設排序
const arrS=[1,122,2,23];
console.log(arrS.sort());//[ 1, 122, 2, 23 ]

//為了比較數字,比較函式可以僅僅利用 a 減 b。以下函式將會升冪排序陣列
arrS.sort( (a, b) => a - b)
console.log(arrS);//[ 1, 2, 23, 122 ]

arrS.sort( (a, b) => b - a)
console.log(arrS);//[ 122, 23, 2, 1 ]
```
