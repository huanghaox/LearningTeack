# Content/更新用户剩余抵押物

在退还了抵押物后，我们还需要记录这笔抵押物的转移。

也就是将这笔金额从调用者的抵押物余额和总额中扣除。

**Syntax**

mapping

- 提示
    
    ```solidity
    remain[msg.sender] -= amount;
    ```
    
