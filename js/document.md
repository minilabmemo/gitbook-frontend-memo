# document

## document.queryselector

利用下方的條件可以選到指定的element，然後對它做style的更動

```go
 //HTML
 <span class="memo" data-speed="1">
      <i class="fas fa-xx"></i>
  </span>
  
  //JS
  const memo = document.querySelector('.memo');
  memo.style.transform = `translateY(${scrollPositionY * moonMoveSpeed}px)`;
  
  //JS 多重選取就要用foreach更變
  let boxes = document.querySelectorAll(".box");
function checkBoxes() {
  boxes.forEach((box) => {
    let boxTop = box.getBoundingClientRect().top;
    if (boxTop < triggerBottom) {
      box.classList.add("show");
    } else {
      box.classList.remove("show");
    }
  });
}
    
```

* 如果發生selector回來的是null，就表示沒有選到，需要檢查這段ＪＳ是否在載入後才執行．
*   原生的ＪＳ放在body後方執行可以取代jQuery的Ready ->[【译】用原生javascript代替jQuery的Ready（）方法](https://www.jianshu.com/p/f359a531a72a)

    \
