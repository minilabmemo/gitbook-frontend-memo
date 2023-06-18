# jest



## 撰寫測試

如果你用react-create-app 生成預設會有一個App.test.tsx

````
```typescriptreact
test('renders learn react link', () => {
  render(<App />);
  const linkElement = screen.getByText(/learn react/i);
  expect(linkElement).toBeInTheDocument();
});
```
裡面是正規表示 代表檢查是否有字體不管大小寫
````

## 執行測試

\`npm test\` 可以執行測試，同時可以邊監控邊執行。

```
 他會自動去抓所有...test的檔案
 PASS  src/components/twDistricts.test.tsx
 PASS  src/App.test.tsx

Test Suites: 2 passed, 2 total
Tests:       3 passed, 3 total
Snapshots:   0 total
Time:        4.385 s
```

## 測試覆蓋率

會多了覆蓋率與未覆蓋的地方。

```
npm test -- --coverage 

 PASS  src/components/twDistricts.test.tsx
 PASS  src/App.test.tsx
------------------|---------|----------|---------|---------|---------------------
File              | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s   
------------------|---------|----------|---------|---------|---------------------
All files         |   81.15 |       50 |   63.63 |   82.35 |                     
 src              |     100 |      100 |     100 |     100 |                     
  App.tsx         |     100 |      100 |     100 |     100 |                     
 src/components   |    80.3 |       50 |    61.9 |   81.53 |                     
  PetFinder.tsx   |   77.08 |      100 |      60 |   77.08 | 150-155,172-191,248 
  header.tsx      |     100 |      100 |     100 |     100 |                     
  twDistricts.tsx |   81.81 |       50 |      60 |      90 | 1629                
------------------|---------|----------|---------|---------|---------------------

Test Suites: 2 passed, 2 total
Tests:       3 passed, 3 total
Snapshots:   0 total
Time:        3.496 s, estimated 4 s
```

