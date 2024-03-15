# Content/引文

上一节在前面的学习当中，我们计算了Lp代币奖励的数量。

这一节，我们要学习要Lp的分发和代币转移流程。在其中，用到了许多ERC20标准的方法，有铸造代币的***_mint***，有转移代币的***transferFrom***等等。

相信你已经迫不及待了，让我们开始吧！

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

    function _calculateAmountB_add(
        uint256 _amountADesierd
    ) internal view returns (uint256) {
        return (reserveB * _amountADesierd) / reserveA;
    }

    function _calculateAmountA_add(
        uint256 _amountBDesierd
    ) internal view returns (uint256) {
        return (reserveA * _amountBDesierd) / reserveB;
    }

    function _addLiquidity(uint256 amountA, uint256 amountB) private {
        uint256 liquidityTokens = calculateLiquidityTokens(amountA, amountB);
    }

    function calculateLiquidityTokens(
        uint256 amountA,
        uint256 amountB
    ) private view returns (uint256 liquidityTokens) {
        uint256 liquidityTokens;
        if (reserveA == 0 && reserveB == 0) {
            liquidityTokens = sqrt(amountA * amountB);
        } else if (reserveA > 0 && reserveB > 0) {
            uint256 liquidityPercentageA = (amountA * totalLiquidity) /
                reserveA;
            uint256 liquidityPercentageB = (amountB * totalLiquidity) /
                reserveB;

            liquidityTokens = (liquidityPercentageA < liquidityPercentageB)
                ? liquidityPercentageA
                : liquidityPercentageB;
        } else {
            revert("Invalid reserve amounts");
        }

        return liquidityTokens;
    }
}
```
