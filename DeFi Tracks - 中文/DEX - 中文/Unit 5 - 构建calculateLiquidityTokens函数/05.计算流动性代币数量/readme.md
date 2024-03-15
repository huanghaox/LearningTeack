# Content/计算流动性代币数量

让我们进入到if语句当中，也就是当流动性池还未初始化时。

这时我们计算***amountA***和***amountB***的**平方根**作为要铸造的***liquidityTokens***的数量。

> 这只是一个模拟情况，真实的DEX项目中将会根据项目白皮书进行计算
> 

平方根的计算我们已经将其抽象为一个单独的函数——***sqrt：***

- code
    
    ```solidity
    function sqrt(uint256 x) private pure returns (uint256 y) {
        // Calculate the square root of a number (rounded down)
        uint256 z = (x + 1) / 2;
        y = x;
        while (z < y) {
            y = z;
            z = (x / z + z) / 2;
        }
    }
    ```
    

**Syntax**

variable

- 提示
    
    ```solidity
    uint moonshot = 520;
    ```
    
