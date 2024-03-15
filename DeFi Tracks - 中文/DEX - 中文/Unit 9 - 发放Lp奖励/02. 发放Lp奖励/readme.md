# Content/发放Lp奖励

在计算出 LP 奖励数量之后，我们需要发放 LP 奖励代币。

你还记得我们为了简化步骤将 ***LiquidityPool*** 合约定义为一个 ERC20 合约吗？这样我们就可以将该合约作为 LP 代币来发行。

由于合约本身就是一个 LP 代币，因此我们可以直接调用 ERC20 的 ***_mint*** 函数来铸造代币，从而完成 LP 代币的发放。

**Syntax**

function call

- 提示
    
    ```solidity
    function mint(address to, uint256 amount) external;
    ```
    
