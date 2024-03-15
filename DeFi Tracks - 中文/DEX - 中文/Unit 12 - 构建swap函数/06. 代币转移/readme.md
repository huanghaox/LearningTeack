# Content/代币转移

在更新完储备量后，我们就来完成swap交换的最后一个步骤——代币的转移。

首先我们需要将***amountA***个***tokenA***从调用者的账户中转移到流动性池。

我们需要使用IERC20接口以完成对***tokenA***代币的调用，将代币从其他账户转移到本地址，我们只用***transferFrom***函数。

我们将***amountA***个代币A从调用者账户转移到了流动性池当中，别忘了我们还要将***amountB***个代币B从流动性池中转移给调用者。

**Syntax**

function call,interface

- 提示
    
    ```solidity
    IERC20(tokenA).transferFrom(msg.sender, address(this), amountA);
    IERC20(tokenB).transfer(msg.sender, amountB);
    ```
    
