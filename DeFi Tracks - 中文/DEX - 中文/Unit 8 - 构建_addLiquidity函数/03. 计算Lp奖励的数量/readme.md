# Content/计算Lp奖励的数量

太好了，现在让我们深入探讨 ***_addLiquidity*** 函数的逻辑。

首先，我们需要计算用户应该获得的 LP 奖励。为了计算 LP 奖励，我们将其抽象为一个单独的函数***calculateLiquidityTokens***，我们已经在第五节讨论了该函数。由于这里是计算 LP 奖励需要添加的流动性数量，因此我们需要将这两个参数分别传递给 ***calculateLiquidityTokens*** 函数。

该函数将返回一个 uint256 类型的值，表示用户应获得的 LP 代币数量。

**Syntax**

function call

- 提示
    
    ```solidity
    uint256 amount = calculateLiquidityTokens(amountA, amountB);
    ```
    
