# Content/Module

[DEX-3.output.mp4](../video/DEX-3.output.mp4)

step1：点击Try it Out进入HackQuest IDE，并编译部署*合约*。（具体步骤可以参考前面章节的教程）。

step2：调用***removeLiquidity***函数

step3：传入参数***liquidityTokens***=*20*

step4：查询***reserveA***和***reserveB***

step5：查询***totalLiquidity***

# Example/示例代码

```jsx
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts@4.9.3/token/ERC20/ERC20.sol";

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

    function addLiquidity(uint256 _amountADesierd, uint256 _amountBDesierd)
        external
    {
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

    function _calculateAmountB_add(uint256 _amountADesierd)
        internal
        view
        returns (uint256)
    {
        return (reserveB * _amountADesierd) / reserveA;
    }

    function _calculateAmountA_add(uint256 _amountBDesierd)
        internal
        view
        returns (uint256)
    {
        return (reserveA * _amountBDesierd) / reserveB;
    }

    function _addLiquidity(uint256 amountA, uint256 amountB) private {
        uint256 liquidityTokens = calculateLiquidityTokens(amountA, amountB);
        _mint(msg.sender, liquidityTokens);
        reserveA += amountA;
        reserveB += amountB;
        totalLiquidity += liquidityTokens;

        IERC20(tokenA).transferFrom(msg.sender, address(this), amountA);
        IERC20(tokenB).transferFrom(msg.sender, address(this), amountB);
    }

    function calculateLiquidityTokens(uint256 amountA, uint256 amountB)
        private
        view
        returns (uint256 liquidityTokens)
    {
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

    function removeLiquidity(uint256 liquidityTokens) external {
        require(
            balanceOf(msg.sender) >= liquidityTokens,
            "liquidity not enough"
        );
        require(totalLiquidity >= liquidityTokens, "Insufficient liquidity");
        _burn(msg.sender, liquidityTokens);
        uint256 amountA = (liquidityTokens * reserveA) / totalLiquidity;
        uint256 amountB = (liquidityTokens * reserveB) / totalLiquidity;

        require(
            IERC20(tokenA).transfer(msg.sender, amountA),
            "Transfer of token A failed"
        );
        require(
            IERC20(tokenB).transfer(msg.sender, amountB),
            "Transfer of token B failed"
        );
        reserveA -= amountA;
        reserveB -= amountB;
        totalLiquidity -= liquidityTokens;
    }

    function sqrt(uint256 x) private pure returns (uint256 y) {
        // Calculate the square root of a number (rounded down)
        uint256 z = (x + 1) / 2;
        y = x;
        while (z < y) {
            y = z;
            z = (x / z + z) / 2;
        }
    }
}

// 定义代币A和代币B

contract MockTokenA is ERC20 {
    constructor() ERC20("TokenA", "HQA") {
        _mint(msg.sender, 10 * 10**18);
    }
}

contract MockTokenB is ERC20 {
    constructor() ERC20("TokenB", "HQB") {
        _mint(msg.sender, 10 * 10**18);
    }
}
```
