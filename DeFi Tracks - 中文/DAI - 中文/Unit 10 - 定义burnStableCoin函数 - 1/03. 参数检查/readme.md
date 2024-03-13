# Content/参数检查

定义完函数头后，我们来写函数体的逻辑吧。
在开始写偿还逻辑之前，我们首先需要做一个参数检查，确保用户传入的要还款的稳定币数量***stableCoinAmount***的值不会超过他从稳定币合约中借出的数量。

因为在超额抵押中，质押物的价值永远大于稳定币的价值，所以我们不希望他可以置换出别人的质押物。

**Syntax**

require

- 提示
    
    ```solidity
    require(amount[msg.sender] > stableAmount, "error");
    ```
    
