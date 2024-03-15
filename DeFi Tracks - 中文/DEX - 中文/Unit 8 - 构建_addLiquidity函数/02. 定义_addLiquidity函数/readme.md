# Content/定义_addLiquidity函数

让我们进入 ***_addLiquidity*** 函数，并首先定义函数头。

首先，我们需要明确该函数的作用：将指定数量的流动性直接添加到流动性池中，并发放 LP 奖励代币。

因此，我们需要两个参数，一个表示 ***TokenA*** 的数量，另一个表示 ***TokenB*** 的数量。

对于函数的可见性修饰符的选择，我们采用 private，因为该函数仅为 ***addLiquidity***函数提供逻辑处理功能。

**Syntax**

function,scope

- 提示
    
    ```solidity
    function _add(uint256 amountA, uint256 amountB) private { }
    ```
    
