# Content/引文

上一章我们利用构造函数初始化了一些状态变量，但是细心的你可能已经发现了，***price***我们并没有初始化！

因为构造函数初始化是一次性的，然而我们知道，现实中的代币价值是时刻变化的，因此我们在本章建立一个函数来给***price***赋值，正如前面所过的，我么使用**预言机**来定义***price***。

# Example/ Code

```solidity
pragma solidity 0.8.17;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

contract SimpleStableCoin is ERC20 {
    IERC20 public collateralToken;
    mapping(address => uint256) public totalCollateral;
    mapping(address => uint256) public remainingCollateral;
    mapping(address => uint256) private loanAmount;
    uint256 public collateralRatio;
    uint256 public liquidationRatio;
    uint256 public price;

    constructor(
        address _collateralToken,
        uint256 _collateralRatio,
        uint256 _liquidationRatio
    ) ERC20("SimpleStableCoin", "SSC") {
        collateralToken = IERC20(_collateralToken);
        collateralRatio = _collateralRatio;
        liquidationRatio = _liquidationRatio;
		
    }
}
```