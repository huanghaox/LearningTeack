# Content/更新用户剩余抵押物

在转移了抵押物后，我们还需要记录这笔抵押物的转移。

换句话说，我们需要给调用者抵押物余额和总额都加上***collateralAmount***。

首先我们来增加余额。

**Syntax**

mapping

- 提示
    
    ```solidity
    remain[msg.sender] += amount;
    ```
    
