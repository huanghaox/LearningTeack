# Content/定义合约并继承ERC20

正如上一步所属，为了简化教程，在导入ERC20标准之后，我们直接将流动性池合约赋予代币功能，即继承 ***ERC20*** 合约，以便提供 LP 奖励。

**Syntax Review**

contract , inherited

- 提示
    
    ```solidity
    pragma solidity ^0.8.0;
    
    contract dex is Moonshot{ }
    ```
    
