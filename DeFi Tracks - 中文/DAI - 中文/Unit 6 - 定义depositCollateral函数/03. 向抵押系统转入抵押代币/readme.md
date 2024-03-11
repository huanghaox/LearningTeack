# Content/向抵押系统转入抵押代币

在之前的步骤中，我们实现了构造函数。现在我们开始编写存抵押物的逻辑。

首先我们需要将抵押物从调用者账户中转移到借贷合约。

由于执行转账的操作者并不是资金的拥有者：合约在转移用户的钱，所以这里我们需要使用ERC20中提供的***transferFrom***接口。将***collateralAmount***数额的抵押物Token转移到借贷合约中。

> ***transferFrom***函数需要用户向借贷合约***approve***一定数额的Token后，借贷合约才能够通过该函数将已授权的一定数额Token从用户账户转移走。
> 

**Syntax**

function call

- 提示
    
    ```solidity
    Token.transferFrom(msg.sender, address(this), amount);
    ```
    
