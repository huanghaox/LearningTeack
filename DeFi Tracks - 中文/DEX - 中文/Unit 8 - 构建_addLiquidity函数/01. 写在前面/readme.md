# Content/引文

当看见_addLiquidity时，你是否有些熟悉？在addLiquidity函数中，它第一个调用的函数就是_addLiquidity。

_addLiquidity函数可以说是addLiquidity的核心了，没有它，我相信整个DEX都无法正常工作。它不仅添加了流动性，还完成了Lp代币的生成与转发……可见，它是多么的强大啊！

这一节，让我们来系统的学习_addLiquidity函数的实现过程吧！

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
                //此时注入的流动性为_amountADesierd和amountBOptimal
                _addLiquidity(_amountADesierd, amountBOptimal);
            } else {
                uint256 amountAOptimal = _calculateAmountA_add(_amountBDesierd);
                //此时注入的流动性为amountAOptimal和_amountBDesierd
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
