# Content/增加储备量

在发放了 LP 奖励之后，让我们回到流动性池的逻辑中。在该函数中，***amountA*** 和 ***amountB*** 分别表示要添加的流动性数量。

所以我们需要将其添加到储备量**reserve**中，在这一步我们分别将***amountA***添加到***reserveA***中，将***amountB***添加到***reserveB***中。

**Syntax**

variable

- 提示
    
    ```solidity
    reserve += amount;
    ```
    
