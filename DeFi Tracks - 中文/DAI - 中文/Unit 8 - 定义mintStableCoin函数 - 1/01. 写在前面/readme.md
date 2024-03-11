# Content/引文

前两章我们已经学习了存取抵押资金的方法，是不是超级简单呢？

但是你想，我们目的是抵押稳定币，目前只是存进去资金了，但是如果获取到稳定币呢？

让我们走进稳定币相关的第一个功能，铸造稳定币，经过刚刚简短的介绍我们知道抵押物换取DAI的过程其实是一个减少用户抵押物余额，铸造稳定币的过程。

让我们进入用来换取DAI的***mintStableCoin***函数吧！

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

    function setPrice(uint256 _price) public {
        price = _price;
    }

    function depositCollateral(uint256 collateralAmount) external {
        collateralToken.transferFrom(
            msg.sender,
            address(this),
            collateralAmount
        );
        remainingCollateral[msg.sender] += collateralAmount;
        totalCollateral[msg.sender] += collateralAmount;
    }

    function withdrawCollateral(uint256 collateralAmount) external {
        require(
            remainingCollateral[msg.sender] >= collateralAmount,
            "Not enough collateral deposited"
        );
        collateralToken.transfer(msg.sender, collateralAmount);
         remainingCollateral[msg.sender] -= collateralAmount;
         totalCollateral[msg.sender] -= collateralAmount;

		}
}
```