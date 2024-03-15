# Content/引文

上一节，我们学习了在流动性池还未初始化的情况下如何计算Lp代币。

这一节，我们将学习初始化后的流动性池该如何计算Lp代币，以及出现了不合法情况该如何处理。

接下来，我们将详细介绍这部分如何实现。

# Example/ Code

```solidity
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract LiquidityPool is ERC20 {
    address public tokenA;
    address public tokenB;

    uint256 public reserveA;
    uint256 public reserveB;
    uint256 public totalLiquidity;

    constructor(address _tokenA, address _tokenB) ERC20("HackQuest", "HQ") {
        tokenA = _tokenA;
        tokenB = _tokenB;
    }

    function addLiquidity(
        uint256 _amountADesierd,
        uint256 _amountBDesierd
    ) external {
        if (reserveA == 0 && reserveB == 0) {
            _addLiquidity(_amountADesierd, _amountBDesierd);
        } else {
            uint256 amountBOptimal = _calculateAmountB_add(_amountADesierd);
            if (amountBOptimal <= _amountBDesierd) {
                _addLiquidity(_amountADesierd, amountBOptimal);
            } else {
                uint256 amountAOptimal = _calculateAmountA_add(_amountBDesierd);
                _addLiquidity(amountAOptimal, _amountBDesierd);
            }
        }
    }

    function calculateLiquidityTokens(
        uint256 amountA,
        uint256 amountB
    ) private view returns (uint256 liquidityTokens) {
        uint256 liquidityTokens;
        if (reserveA == 0 && reserveB == 0) {
            liquidityTokens = sqrt(amountA * amountB);
        } else {}
    }
}
```