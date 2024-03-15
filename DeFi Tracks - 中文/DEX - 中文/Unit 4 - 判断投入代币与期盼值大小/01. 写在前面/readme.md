
# Content/引文

好的，上一节我们对**DEX**添加流动性有了大致的了解。

**添加流动性**是并不是一件简单的事哦！上一节知道了用户加入一定量A代币时应该加入多少B代币。可是它的用处是什么呢？

这一节，我们通过计算实际理论代币数量和投入代币数量来添加流动性！

接下来，带着这些思考让我们继续完善它的功能吧！

# Example/ Code

```solidity
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract LiquidityPool is ERC20{ 
		address public tokenA;
    address public tokenB;

		uint256 public reserveA;
    uint256 public reserveB;
		uint256 public totalLiquidity;

		constructor(address _tokenA, address _tokenB) ERC20("HackQuest", "HQ") { 
				tokenA = _tokenA;
        tokenB = _tokenB;
		}

		function addLiquidity(uint256 _amountADesierd, uint256 _amountBDesierd) external {
				if (reserveA == 0 && reserveB == 0) {
            _addLiquidity(_amountADesierd, _amountBDesierd);
				} else {
						
				}
		}
}
```
