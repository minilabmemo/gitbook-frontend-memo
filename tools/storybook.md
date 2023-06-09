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

#### 生成

完成後會多出.storybook與 src/stories 這裡面有很多預設的範例,可以刪掉自己創建

## 啟動

<pre><code>npm run storybook
<strong>http://localhost:6006/?path=/story/example-button--secondary
</strong></code></pre>

