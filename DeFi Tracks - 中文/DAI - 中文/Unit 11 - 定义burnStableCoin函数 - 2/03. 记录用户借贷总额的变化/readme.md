# Content/记录用户借贷总额的变化

在归还了用户的抵押物后，我们还需要将稳定币回收，也就是烧毁，在烧毁之前，我们还需要记录用户归还的这笔稳定币。

也就是在用户的借贷总额中减去这笔归还的金额***stableCoinAmount***。

**Syntax**

mapping

- 提示
    
    ```solidity
    loan[msg.sender] -= stableAmount;
    ```
    
