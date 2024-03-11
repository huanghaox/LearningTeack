# Content/引文

前两章我们已经将合约的大致结构建立好了，但是你有没有发现有些变量没有赋值！另外在上一节我们引入了ERC20合约，也并没有派上用场，这一节我们利用构造函数来初始化状态变量。

接下来，我们将详细介绍如何使用构造函数。

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

}
```