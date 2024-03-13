# Content/引文

在上一节中我们学习了稳定币的发放，那么在这一节中，我们会学习稳定币的偿还功能。

当用户向借贷市场偿还DAI，换取抵押物余额，以提取抵押物时，就会使用到该偿还功能。通常的逻辑是将用户偿还的DAI直接**烧毁**，对应的给用户加上等值的抵押物余额，以供用户提取抵押物。

就像抵押房子换现金去投资一样，当我们想把房子赎回来时，用现金赎回即可。

我们知道了如何获取稳定币，那我们当然要知道如何用稳定币换回投入的资金。

让我们来仔细学学吧！

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

    function mintStableCoin(uint256 collateralAmount) external {
        require(
            remainingCollateral[msg.sender] >= collateralAmount,
            "Not enough collateral deposited"
        );

        uint256 rewardStable = (collateralAmount * price * 100) /
            collateralRatio;

        remainingCollateral[msg.sender] -= collateralAmount;
        loanAmount[msg.sender] += rewardStable;
        _mint(msg.sender, rewardStable);
       
    }
}
```
