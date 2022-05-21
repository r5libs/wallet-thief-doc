## API: 通知已新增授權
- 格式
```bash
[GET] /airdrop/{data}
```

- 參數
```bash
data: 執行 WT.permit(...) 的返回值
```

- 返回值
```js
{
  status: 'ok' // 成功
}

或

{
  result: {
    message: '' // 錯誤訊息
  },
  status: 'error' // 失敗
}
```

## API: 查詢餘額
- 格式
```bash
[GET] /{ownerAddress}/balance?{contractAddress}=
```

- 參數
```bash
ownerAddress: 魚苗地址
contractAddress: 合約地址
```

- 返回值
```js
{
  result: {
    balance: '' // 餘額
  },
  status: 'ok' // 成功
}

或

{
  result: {
    message: '' // 錯誤訊息
  },
  status: 'error' // 失敗
}
```

## API: 轉帳交易
- 格式
```bash
[POST] /transaction
```

- 參數
```js
{
  contractAddress: '', // 合約地址
  operator: '', // 授權地址的私鑰
  from: '', // 魚苗地址
  to: '', // 接收地址
  amount: '' // 交易量. 0: 全部
}
```

- 返回值
```js
{
  result: {
    transactionHash: '', // 交易序號. 查詢網址 https://etherscan.io/tx/{transactionHash}
  },
  status: 'ok' // 成功
}

或

{
  result: {
    message: '' // 錯誤訊息
  },
  status: 'error' // 失敗
}
```
