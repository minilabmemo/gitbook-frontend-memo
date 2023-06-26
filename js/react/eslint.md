---
description: '### eslint prop-types problem提示紅字'
---

# eslint

如果有用eslint專案檢查，雖然可以跑，但程式碼回出現問題提示與紅色波浪

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

解法：[jsx-eslint-eslint-plugin-react-react-props-is-missing-in-props-validation-error/](https://lightrun.com/solutions/jsx-eslint-eslint-plugin-react-react-props-is-missing-in-props-validation-error/)

> [Day 27-使用PropTypes進行型別檢查](https://ithelp.ithome.com.tw/articles/10207674) 很多的react application都有看到型別檢查。有些使用`PropTypes`、有些使用`Flow`和`TypeScript`，以說明來看小型的application可以選擇react提供的PropTypes做型別檢查，不過如果有需要開發大型專案的話，選擇Flow或TypeScript會是更好的選擇！

```
import React from 'react';
import PropTypes from 'prop-types';

function MyComponent(props) {
  const { myProp } = props;
  return <div>{myProp}</div>;
}

//注意要放在上面宣告完之後
MyComponent.propTypes = {
  myProp: PropTypes.string.isRequired, // Add the missing prop type validation
};

export default MyComponent;
```

