# Content/引文

好了，在前两节我们已经实现了***LiquidityPool***合约的初始化以及状态变量的定义。

这一节，让我们来试着给这个***LiquidityPool***添加一些功能吧！

现在，我们将为**DEX**添加功能。作为一个**DEX**，**流动性**是最关键的要素之一。因此，我们首先需要定义一个用于添加流动性的功能。这个功能的目的是为用户提供一个调用**接口**，以便他们能够向DEX提供流动性。

作为对流动性提供者的激励，我们将奖励一部分的Lp代币给他们。Lp 代币在DEX生态系统中具有重要的价值。

接下来，我们将详细介绍如何实现这个添加流动性的功能

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
}
```