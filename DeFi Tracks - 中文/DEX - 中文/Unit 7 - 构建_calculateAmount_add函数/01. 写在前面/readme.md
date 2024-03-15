# Content/引文

还记得在***addLiquidity***函数中我们计算***amountBOptimal***调用的函数吗？它的作用：是在已知投入固定量A代币时，应该投入多少B代币。毕竟添加流动性时本就要保持代币的比例一致。这一节，我们就要学习这个函数的实现。

接下来，让我们来完成它吧！

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
            uint256 amountBOptimal = _calculateAmountB(_amountADesierd);
            if (amountBOptimal <= _amountBDesierd) {
                //此时注入的流动性为_amountADesierd和amountBOptimal
                _addLiquidity(_amountADesierd, amountBOptimal);
            } else {
                uint256 amountAOptimal = _calculateAmountA(_amountBDesierd);
                //此时注入的流动性为amountAOptimal和_amountBDesierd
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