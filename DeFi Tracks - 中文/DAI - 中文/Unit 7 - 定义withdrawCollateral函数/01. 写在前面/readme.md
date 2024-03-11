# Content/引文

在上一节中，我们学到了如何将抵押物存入借贷合约，那么相应的我们就需要一个**取出抵押物**的功能。

在本节中，我们将实现稳定币合约的第二个功能：将抵押品从合约中取出。 

当我们希望取出抵押物时就可以归还稳定币以将抵押品取出，需要注意的是抵押物不能随时被取出，只有当你偿还了一定的贷款后，才可以取出相应的抵押物。

那么接下来我们来尝试实现这个逻辑吧。

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
}
```