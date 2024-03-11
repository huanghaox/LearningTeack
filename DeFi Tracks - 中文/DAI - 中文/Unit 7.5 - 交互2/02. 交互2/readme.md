# Content/Module

[DAI-u5-output.mp4](../video/DAI-u5-output.mp4)

1. 点击Try it Out 进入HackQuest IDE，部署***MockToken***合约。
2. 将***MockToken***合约的地址作为***SimpleStableCoin***构造函数的参数，部署***SimpleStableCoin***合约。
3. 打开***MockToken***合约的下拉框，将***SimpleStableCoin***合约地址复制到MockToken的***approve***函数第一个参数的位置，授权大于*1*个代币。
4. 收起***MockToken***合约，打开***SimpleStableCoin***合约下拉框，找到***depositCollateral***函数，输入*1*点击调用。
    
    > 存入质押物
    > 
5. 查询当前用户状态，包括稳定币余额，抵押物余额等信息。
6. 打开***withdrawCollateral***合约的下拉框，输入*1*点击调用。
    
    > 取出质押物
    > 
7. 查询当前用户状态，包括稳定币余额，抵押物余额等信息。

# Example/示例代码

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.17;

import "@openzeppelin/contracts@4.9.3/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts@4.9.3/token/ERC20/IERC20.sol";

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

contract MockToken is ERC20 {
    constructor() ERC20("HackQuest", "HQ") {
        _mint(msg.sender, 10 * 10 ** 18);
    }
}
```