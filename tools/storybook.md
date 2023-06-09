# storybook

## 專案

需要先有一個專案,網路上有各種方式可以快速生成一個範例專案,如果你已經有就不用了

```
官方
# Clone the template
npx degit chromaui/intro-storybook-react-template taskbox
# Install dependencies
yarn


網路教學用vite起
npm create vite@latest 你的專案名稱 -- --template react && npm install

```



## 安裝

在一個現有專案下下這個指令：

* \`npx storybook@latest init\` at 官方 [https://storybook.js.org/docs/react/get-started/install/](https://storybook.js.org/docs/react/get-started/install/)
* \`npm sb init\` at web
* \`npx sb init --builder @storybook/builder-vite\` at youtuber&#x20;
* \`npx -p [@storybook/cli](http://twitter.com/storybook/cli) sb init\`

```
$ npx sb init
Need to install the following packages:
  sb@7.0.20
Ok to proceed? (y) y
? We have detected that you're using ESLint. Storybook provides a plugin that gives the best experience with Storybook and helps follow best practices: https://github.com/storybookjs/eslint-plugin-storybook#readme

Would you like to install it? › (Y/n)
  ✔ Installing Storybook dependencies
. ✓
 • Preparing to install dependencies. ✓


npm ERR! code ERESOLVE
npm ERR! ERESOLVE could not resolve
npm ERR! 
npm ERR! While resolving: @mui/styles@5.13.2
npm ERR! Found: react@18.2.0
npm ERR! node_modules/react
npm ERR!   react@"^18.2.0" from the root project
npm ERR!   peer react@">=16.8.0" from @emotion/react@11.11.0
npm ERR!   node_modules/@emotion/react
npm ERR!     @emotion/react@"^11.11.0" from the root project
npm ERR!     peer @emotion/react@"^11.0.0-rc.0" from @emotion/styled@11.11.0
npm ERR!     node_modules/@emotion/styled
npm ERR!       @emotion/styled@"^11.11.0" from the root project
npm ERR!       4 more (@mui/material, @mui/styled-engine, @mui/system, react-material-ui-carousel)
npm ERR!     4 more (@mui/material, @mui/styled-engine, @mui/system, react-material-ui-carousel)
npm ERR!   46 more (@emotion/styled, ...)
npm ERR! 
npm ERR! Could not resolve dependency:
npm ERR! peer react@"^17.0.0" from @mui/styles@5.13.2
npm ERR! node_modules/@mui/styles
npm ERR!   @mui/styles@"^5.13.2" from the root project
npm ERR! 
npm ERR! Conflicting peer dependency: react@17.0.2
npm ERR! node_modules/react
npm ERR!   peer react@"^17.0.0" from @mui/styles@5.13.2
npm ERR!   node_modules/@mui/styles
npm ERR!     @mui/styles@"^5.13.2" from the root project
npm ERR! 
npm ERR! Fix the upstream dependency conflict, or retry
npm ERR! this command with --force or --legacy-peer-deps
npm ERR! to accept an incorrect (and potentially broken) dependency resolution.
npm ERR! 
npm ERR! 
npm ERR! For a full report see:
npm ERR! /Users//.npm/_logs/2023-06-09T03_09_38_937Z-eresolve-report.txt

npm ERR! A complete log of this run can be found in: /Users//.npm/_logs/2023-06-09T03_09_38_937Z-debug-0.log
. ✖

     An error occurred while installing dependencies.

attention => Storybook now collects completely anonymous telemetry regarding usage.
This information is used to shape Storybook's roadmap and prioritize features.
You can learn more, including how to opt-out if you'd not like to participate in this anonymous program, by visiting the following URL:
https://storybook.js.org/telemetry

```

這邊安裝有報一些錯 不過還是有成功，之後再看。TODO

### 生成檔案與指令

完成後會多出.storybook與 src/stories 這裡面有很多預設的範例,可以刪掉自己創建

````diff
```json
  "scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build",
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
+    "eject": "react-scripts eject",
+    "storybook": "storybook dev -p 6006",
+    "build-storybook": "storybook build"
  },
```
````

## 啟動

<pre><code>npm run storybook
<strong>http://localhost:6006/?path=/story/example-button--secondary
</strong></code></pre>



## 範例

可以看我儲存的github網路上的範例．

#### 用js寫的範例

[https://braedongough.medium.com/how-to-add-storybook-to-a-typescript-create-react-app-project-28aa99c9943e](https://braedongough.medium.com/how-to-add-storybook-to-a-typescript-create-react-app-project-28aa99c9943e)

```
/1-Button.stories.js
import React from 'react';
import { action } from '@storybook/addon-actions';
import { Button } from '@storybook/react/demo';

export default {
  title: 'Button',
  component: Button,
};

export const Text = () => <Button onClick={action('clicked')}>Hello Button</Button>;

export const Emoji = () => (
  <Button onClick={action('clicked')}>
    <span role="img" aria-label="so cool">
      😀 😎 👍 💯
    </span>
  </Button>
);
```

#### 用tsx寫的範例

[https://dev.to/sanchithasr/how-to-implement-storybook-in-react-typescript-material-ui-application-4om7](https://dev.to/sanchithasr/how-to-implement-storybook-in-react-typescript-material-ui-application-4om7)

```
import TextButton from "./Button"
import { ComponentMeta, ComponentStory} from "@storybook/react"

export default {
    title: "Components/Button",
    component: TextButton,
} as ComponentMeta<typeof TextButton>

const Template: ComponentStory<typeof TextButton> = (args) => <TextButton {...args} />;

export const Submit = Template.bind({});
Submit.args = {
  label: 'Button',
};

export const Check = Template.bind({});
Check.args = {
  label: 'Check',
};
```

#### 較新的寫法 tsx

````
```typescriptreact

export default {
  title: 'Tooltip',
  component: Tooltip,
  // 調整 story 的呈現的位置， https://storybook.js.org/docs/react/configure/story-layout
  parameters: {
    layout: 'centered',
  },
} as Meta<typeof Tooltip>;

export const Raw = () => (
  <div style={{ display: 'flex', alignItems: 'center', justifyContent: 'center', height: 160, width: 300 }}>

    <Tooltip
      content={<div><div>Tooltip</div><div>test!</div></div>}
      placement="top"
      gap={12}
      color={'red'}
    >
      <Button variant="outlined">
        Bottom Raw
      </Button>

    </Tooltip>

  </div >
);

//Template 寫法 這裡面參數在畫面上是可以改的
const Template: StoryFn<typeof Tooltip> = (args) => (
  <Tooltip
    {...args}
  >
    <Button variant="outlined">
      Buttom
    </Button>

  </Tooltip>

);

//置換 Template 的參數
export const Bottom = Template.bind({});
Bottom.args = {
  placement: 'bottom',
  content: <div><div>Tooltip</div><div>test!</div></div>,
  showArrow: true
};


```
````

## 優點

{% hint style="info" %}
採用這個可以從畫面上的control頁直接操控變數args,不用去從程式碼上面一直改,也可以找出不合理的地方

```typescriptreact
XX showArrow?: boolean | null, //我真的這樣寫
OO showArrow?: boolean , 其實只有兩種
畫面就會幫你變成切換開關的設定
```
{% endhint %}

## 進階設定

### 自訂control中下拉選項 argTypes



{% hint style="danger" %}
* 這邊要注意打錯字看不到效果,也沒有錯誤出現
* 但應該會有提示文字 照提示文字打
{% endhint %}

````
xxx.stories.tsx
```typescriptreact
export default {
  title: 'MyComponentName',
  component: Tooltip,
  // 調整 story 的呈現的位置， https://storybook.js.org/docs/react/configure/story-layout
  parameters: {
    layout: 'centered',
  },
  
  //https://storybook.js.org/docs/react/essentials/controls
  argTypes: {
    myPropsName: {
      options: ['1', '2'],
      control: { type: "select" }
    },
  }
} as Meta<typeof MyComponentName>;
```
````

### 設定decorators

```
.storybook/preview.tsx
https://storybook.js.org/docs/react/writing-stories/decorators

你可以修改這格檔案decorators來改變story被生成的全域設定  例如全域樣式 置中顯示之類的

//傳入Story與放置位置
 decorators: [
    (Story) => (
      <ThemeProvider theme="default">
        {/* 
👇
 Decorators in Storybook also accept a function. Replace <Story/> with Story() to enable it  */}
        <Story />
      </ThemeProvider>
    ),
    
```

##
