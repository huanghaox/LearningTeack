# Content/定义addLiquidity函数

到目前为止，我们已经做好了写***addLiquidity***函数的前置准备，包括变量的定义和赋值。

现在就让我们来定义***addLiquidity***函数吧，首先我们需要明白该函数的功能：指定想要添加的流动性数量，合约会按照需求来将符合代币比例的流动性注入流动性池当中。

> 我们不能直接将用户输入的流动性数量直接添加进流动性池中，这会导致DEX币价的波动。
> 

所以我们需要两个入参，分别表示***tokenA***的数量和***tokenB***的数量。

在可见性上我们选择external，因为在这是一个对外提供功能的函数。

**Syntax Review**

function

- 提示
    
    ```solidity
    function moonshot(uint256 _amountA, uint256 _amountB) external { }
    ```
    
