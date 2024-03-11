# Content/退还抵押物

在我们确保调用者确实拥有***collateralAmount***数量的抵押物余额后，我们就需要将抵押物退还给调用者。

这里我们需要使用抵押物代币***collateralToken***的***transfer***函数，来将相应数量的抵押物退还给调用者。

**Syntax**

function call

- 提示
    
    ```solidity
    Token.transfer(msg.sender, amount);
    ```
    
