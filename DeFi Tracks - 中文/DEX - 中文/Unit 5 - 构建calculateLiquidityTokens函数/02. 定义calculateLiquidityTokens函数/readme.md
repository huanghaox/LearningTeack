# Content/定义calculateLiquidityTokens函数

该函数应接受两个参数 ***amountA*** 和 ***amountB***。由于该函数不修改合约状态，我们选择使用 view 修饰。

在可见性修饰符的选择上，我们选择使用 private，因为该函数是合约内部逻辑的处理函数。

**Syntax**

function , scope

- 提示
    
    ```solidity
    function calculate(uint256 amountA, uint256 amountB) private view returns(uint256 liquidity) { }
    }
    ```
    
