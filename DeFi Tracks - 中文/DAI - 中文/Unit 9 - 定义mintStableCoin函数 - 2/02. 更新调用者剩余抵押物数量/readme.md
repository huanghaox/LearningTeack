# Content/更新调用者剩余抵押物数量

到此为止，我们已经确定了调用者要兑换的稳定币需要扣除多少**抵押物**，并且确定调用者确实有能力支付这笔抵押物。

我们可以直接将该笔抵押物从调用者账户中扣除，也就是从***remainingCollateral***映射中扣除。

**Syntax**

mapping

- 提示
    
    ```solidity
    remaining[msg.sender] -= collateralAmount;
    ```
    
