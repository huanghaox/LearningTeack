# Content/定义removeLiquidity函数

我们来定义一个***removeLiquidity***函数，该函数的作用是从流动性池中移除流动性代币。移除流动性代币意味着用户可以提取对应的资产。

为了使用这个函数，你需要传入一个uint256类型的参数***liquidityTokens***，表示你要移除的流动性代币的数量。这个参数将用于确定你想要提取的流动性代币数量。

为了使该函数可以被其他合约或外部调用者使用，我们将选择`external`可见性。这意味着该函数可以从其他合约中调用，也可以从合约外部进行交互。

**Syntax**

function , scope

- 提示
    
    ```solidity
    function removeLiquidity(uint256 liquidityTokens) external { }
    ```
    
