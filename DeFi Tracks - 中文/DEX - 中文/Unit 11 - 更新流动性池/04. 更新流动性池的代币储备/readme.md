# Content/更新流动性池的代币储备

好了，我们刚刚已经将对应的***tokenA***和***tokenB***的资金从流动性池中转给了用户，完成了提款。

最后别忘了更新流动性池的储备量 - 分别更新***reserveA***和***reserveB***。

**Syntax**

variable

- 提示
    
    ```solidity
    reserve -= amount;
    ```
    
