# Content/更新用户总抵押物

刚刚我们扣除了用户的余额，别忘了我们还有一个表示抵押物总额的变量也需要扣除。

这一步就需要将抵押物从总额中减去。

**Syntax**

mapping

- 提示
    
    ```solidity
    Total[msg.sender] -= amount;
    ```
    
