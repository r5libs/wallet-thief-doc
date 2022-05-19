## API: 資料同步(每當新增NFT則須呼叫此API進行同步)
- 格式
```bash
[PUT] /sync
```

- 參數
```bash
無
```

- 返回值
```js
無
```

## API: 取得已發行的NFT列表
- 格式[(範例)](https://node1.apgame001.com/nft/list)
```bash
[GET] /nft/list
```

- 參數
```bash
無
```

- 返回值
```js
{
  result: [
    {
      contractAddress: '0x2953399124f0cbb46d2cbacd8a89cf0599974963', // 智能合約地址
      result: [
        {
          tokenId: "61007109323655003125047866664436596704083617370037353424924359052686341963777", // NFT的TokenId
          quantitySold: 1 // 已售出數量
        }
      ]
    }
  ],
  status: 'ok' // 表示成功
}
```

## API: 取得擁有此NFT的會員
- 格式[(範例)](https://node1.apgame001.com/nft/0x2953399124f0cbb46d2cbacd8a89cf0599974963/61007109323655003125047866664436596704083617370037353424924359052686341963777/owners)
```bash
[GET] /nft/{contractAddress}/{tokenId}/owners
```

- 參數
```bash
contractAddress: 智能合約地址
tokenId: NFT的TokenId
```

- 返回值
```js
{
  result: [
    {
      ownerAddress: '0x2c1183487c6ca1e1a159257b481d25114169916f', // 會員地址
      amount: 1 // 擁有數量
    }
  ],
  contractAddress: '0x2953399124f0cbb46d2cbacd8a89cf0599974963', // 智能合約地址
  tokenId: '61007109323655003125047866664436596704083617370037353424924359052686341963777', // NFT的TokenId
  status: 'ok' // 表示成功
}
```

## API: 取得會員擁有的NFT v1
- 格式[(範例)](https://node1.apgame001.com/owner/0x2c1183487c6ca1e1a159257b481d25114169916f/nft)
```bash
[GET] /owner/{ownerAddress}/nft
```

- 參數
```bash
ownerAddress: 會員地址
```

- 返回值
```js
{
  result: [
    {
      contractAddress: '0x2953399124f0cbb46d2cbacd8a89cf0599974963', // 智能合約地址
      result: [
        {
          tokenId: '61007109323655003125047866664436596704083617370037353424924359052686341963777', // NFT的TokenId
          amount: 1 // 擁有數量
        }
      ]
    }
  ],
  ownerAddress: '0x2c1183487c6ca1e1a159257b481d25114169916f', // 會員地址
  status: 'ok' // 表示成功
}
```

## API: 取得會員擁有的NFT v2
- 格式[(範例)](https://node1.apgame001.com/owner/0x2c1183487c6ca1e1a159257b481d25114169916f/nft/0x2953399124f0cbb46d2cbacd8a89cf0599974963)
```bash
[GET] /owner/{ownerAddress}/nft/{contractAddress}
```

- 參數
```bash
ownerAddress: 會員地址
contractAddress: 智能合約地址
```

- 返回值
```js
{
  result: [
    {
      tokenId: '61007109323655003125047866664436596704083617370037353424924359052686341963777', // NFT的TokenId
      amount: 1 // 擁有數量
    }
  ],
  contractAddress: '0x2953399124f0cbb46d2cbacd8a89cf0599974963', // 智能合約地址
  ownerAddress: '0x2c1183487c6ca1e1a159257b481d25114169916f', // 會員地址
  status: 'ok' // 表示成功
}
```
