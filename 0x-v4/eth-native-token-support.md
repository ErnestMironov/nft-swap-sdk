---
description: Sell an NFT for ETH. Buy an NFT with ETH.
---

# ETH/Native Token support

Swap SDK & 0x v4 NFT fully support buying NFTs using ETH (or the native token if not on mainnet).&#x20;

Since ETH (or any native token on the EVM) is not technically an ERC20 (and doesn't have a 'token address'), we work around that by using a 'fake' address for ETH.



To require filling an order with ETH, hardcode the `tokenAddress` to `0xeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee` (the common ERC20 representation of ETH)

```
const orderWithEth = nftSwap.buildOrder(
  // NFT is for sale for    
  { type: 'ERC721', tokenAddress: '0xa0b8...', tokenId: '401' },
  // In exchange for 1 ETH  
  { type: 'ERC20', tokenAddress: '0xeeee...', amount: '1e18' },
  MAKER_WALLET_ADDRESS,
);
```

From there, you can fill this order as usual (e.g. `nftSwap.fillSignedOrder(...)`)



### Native Tokens

Native token can vary with the EVM chain, although the underlying concept remains the same. It is the primary token that is used to pay gas fees and other transaction fees.

Mainnet: `ETH`

Ropsten: `ETH`

Polygon: `MATIC`

Optimism: `OETH`

BSC: `BNB`
