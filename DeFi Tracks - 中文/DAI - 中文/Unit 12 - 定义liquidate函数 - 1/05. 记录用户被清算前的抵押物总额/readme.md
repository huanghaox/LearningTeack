# Content/记录用户被清算前的抵押物总额

当程序继续执行时，也就意味着该地址符合了清算的条件，接下来的逻辑就是对该地址进行清算了。

在清空用户的抵押物之前，我们还需要先记录一下该地址拥有的抵押物总额，这是为了给最后一步给清算者发放奖励做铺垫。

**Syntax**

variable mapping

- 提示
    
    ```solidity
    uint256 liquidatedAmount = totalCollateral[user];
    ```
    
