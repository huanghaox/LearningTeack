# Content/引文

上一节，我们已经烧毁了代币，但是不能只烧毁吧。只烧毁并没有什么反馈的话谁也不愿意凭空烧毁啊！

因此要以烧毁Lp代币计算并转给用户资金，做完这些肯定远远不够，流动性池的存储量总是因为各种处理而改变，所以我们总是要记得**及时更新**流动性池！

接下来，让我们学习烧毁Lp代币后的处理吧！

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
        _mint(msg.sender, liquidityTokens);
        reserveA += amountA;
        reserveB += amountB;
        totalLiquidity += liquidityTokens;

        IERC20(tokenA).transferFrom(msg.sender, address(this), amountA);
        IERC20(tokenB).transferFrom(msg.sender, address(this), amountB);
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

    function removeLiquidity(uint256 liquidityTokens) external {
        require(
            balanceOf(msg.sender) >= liquidityTokens,
            "liquidity not enough"
        );
        require(totalLiquidity >= liquidityTokens, "Insufficient liquidity");
        _burn(msg.sender, liquidityTokens);
    }
}
```