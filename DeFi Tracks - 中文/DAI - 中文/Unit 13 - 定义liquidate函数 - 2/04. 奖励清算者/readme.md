# Content/奖励清算者

到这里，我们就完成了对***user***的清算。但别忘了，我们还需要奖励清算者。

这里的奖励逻辑在之前提到过，其实是将***user***用户之前的抵押物的一部分奖励给清算者。

> 由于实现奖励的计算过于复杂，我们在这里直接将抵押物全部奖励给清算者
> 

在这里只需要将***liquidatedCollateral***数量的***collateralToken***转给**调用者**即可***。***

**Syntax**

function call

- 提示
    
    ```solidity
    transfer(msg.sender, amount);
    ```
    
