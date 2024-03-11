# Content/判断抵押物数量是否合法

首先我们需要进行一个条件判断。因为我们希望在抵押物余额不足时，拒绝用户本次的稳定币兑换。

所以我们在这里需要判断用户的抵押物余额***remainingCollateral***的值是否大于等于***collateralAmount***的值。

**Syntax**

require

- 提示
    
    ```solidity
    require(remainingCollateral[msg.sender] >= requiredCollateral, "error");
    ```
    
