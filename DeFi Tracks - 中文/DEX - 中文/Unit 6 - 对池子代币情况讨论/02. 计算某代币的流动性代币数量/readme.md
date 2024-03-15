# Content/计算某代币的流动性代币数量

现在让我们进入到else分支，这是已初始化的流动性池的计算逻辑。

在这里我们有一个计算模型，内容如下：

先分别计算***amountA***和***amountB***占其储备量的份额乘上总流动性，最后取较小的比值作为Lp奖励代币的数量。

> 计算逻辑每个项目会有不同，我们只是示范了最简单的一个计算模型。
> 

**Syntax**

variable

- 提示
    
    ```solidity
    uint256 Percentage = (amount * totalLiquidity) / reserve;
    ```
    
