 Content/引文

好了，前两节我们知道了添**加流动性的过程**，但是你知道添加流动性时具体发生了什么吗？

这一节，我们来探讨一下**DEX**中超级重要的计算流动性代币吧！你应该知道，我们在添加了流动性后，会有相应的Lp代币生成并分发给我们，它相当于我们添加流动性后在**DEX**中的一个“股份”。当然，如何初始化以及初始化后该如何计算流动性代币也是本节一大课题，学了这部分后，我相信你就能对流动性代币的产生方式了然于胸！

接下来，我们将详细介绍如何定义这个函数以及如何记录Lp代币产生的数量吧！

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
}
```