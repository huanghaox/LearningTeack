# Content/计算应转回给用户的代币数量

在前面的步骤中，我们已经成功烧毁了用户持有的Lp奖励代币。现在，我们将计算根据用户烧毁的Lp代币数量，他们应该能够提取多少代币A和代币B。

在这一步中，我们需要进行两个计算，分别是***amountA***和***amountB***的计算。这些值将根据用户烧毁的Lp代币占总Lp发行量的比例和代币A、代币B的储备量来确定。

具体计算公式如下：

```solidity
amountA = （烧毁的Lp代币数量 / 总Lp发行量） * 代币A的储备量

amountB = （烧毁的Lp代币数量 / 总Lp发行量） * 代币B的储备量
```

> 但是注意，在代码中的计算不能这么写，在solidity中会存在除法截断，因为它总是向下取整，所以像遇到这种先除后乘的计算时，为了减小计算误差，我们通常使用先乘后除的方式。
> 

**Syntax**

variable

- 提示
    
    ```solidity
    uint256 amount = (liquidityTokens * reserve) / totalLiquidity;
    ```
    
