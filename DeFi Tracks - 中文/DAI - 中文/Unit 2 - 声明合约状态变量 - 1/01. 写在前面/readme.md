# Content/引文

上一章我们已经定义了DAI合约的基本结构，那么这一章让我们来声明一下合约中需要的状态变量吧！

首先你要知道，状态变量是合约中声明的存储数据的变量，它们的值在整个合约的生命周期中持久存在于区块链上。有了这些必要变量的加入，我们的借贷系统才能够正常运作！

好了，让我们开始吧！

# Example/ Code

```solidity
pragma solidity 0.8.17;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

contract SimpleStableCoin is ERC20 {}

```