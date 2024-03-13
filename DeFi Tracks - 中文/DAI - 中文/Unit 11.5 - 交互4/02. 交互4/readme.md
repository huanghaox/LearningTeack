# Content/Module

[DAI2-u6-output.mp4](../video/DAI2-u6-output.mp4)

step1：击Try it Out 进入HackQuest IDE，部署***MockToken***合约。

step2：将***MockToken***合约的地址作为***SimpleStableCoin***构造函数的第一个参数，第二个参数质押率为*150*。部署***SimpleStableCoin***合约

step3：打开***MockToken***合约的下拉框，将***SimpleStableCoin***合约地址复制到MockToken的approve函数第一个参数的位置，授权大于**1**个代币。

step4：收起***MockToken***合约，打开***SimpleStableCoin***合约下拉框，找到***depositCollateral***函数，输入*1*点击调用。

> 存入质押物
> 

step5：调用***setPrice***函数，将价格设置为*99*。

> 这一步需要在换取稳定币之前完成
> 

step6：随后找到***mintStableCoin***函数，输入*1*点击调用。

> 换取稳定币
> 

step7：查询当前用户状态，包括稳定币余额，抵押物余额等信息。

step8：找到***burnStableCoin***函数，输入参数*66*调用。

> *66*为我们目前的稳定币余额，我们将全部稳定币全部提取出来
> 

step9：查询当前用户状态，包括稳定币余额，抵押物余额等信息。

# Example/示例代码

```solidity
// SPDX-License-Identifier: MIT
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

    function burnStableCoin(uint256 stableCoinAmount) external {
        require(
            loanAmount[msg.sender] >= stableCoinAmount,
            "incorrect parameter"
        );
        uint256 returnedCollateral = (stableCoinAmount * collateralRatio) /
            100 /
            price;
        remainingCollateral[msg.sender] += returnedCollateral;
        loanAmount[msg.sender] -= stableCoinAmount;
        _burn(msg.sender, stableCoinAmount);
    }
}

contract MockToken is ERC20 {
    constructor() ERC20("HackQuest", "HQ") {
        _mint(msg.sender, 10 * 10**18);
    }
}
```