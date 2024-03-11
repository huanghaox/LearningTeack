# Content/定义合约并继承ERC20

正如上一步所说，为了简化教程，在导入ERC20标准之后，我们直接将DAI合约赋予代币功能，即继承ERC20合约，以便提供代币的**抵押**功能。

这是上述使用OpenZeppelin的ERC20的第二步。

**Syntax**

contract inherited

- 提示
    
    ```solidity
    contract DAI is Moonshot{ }
    ```
    
