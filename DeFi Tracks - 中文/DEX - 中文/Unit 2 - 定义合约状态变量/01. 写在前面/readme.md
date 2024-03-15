# Content/引文

好了，上一节我们已经写好了合约的结构，这一节我们来定义一些状态变量来**记录**数据吧。

首先你要知道，状态变量是合约中声明的存储数据的变量，它们的值在整个合约的生命周期中持久存在于区块链上。而我们要写的是一个自动化做市商模型，自然也需要一些变量来记录数据。

其次，在上一节我们引入了***ERC20***合约，但是并没有派上用场，这一节我们利用构造函数来命名我们的Lp代币以及符号。

接下来，我们将详细介绍如何声明状态变量和构造函数。

# Example/ Code

```solidity
pragma solidity ^0.8.0;
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract LiquidityPool is ERC20 {}
```
