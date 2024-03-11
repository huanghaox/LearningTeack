# Content/为调用者发放稳定币

最后一步只需要给用户铸造***rewardStable***数量的稳定币即可。

还记得我们继承了ERC20合约吗，在标准的ERC20的实现中，都有一个内置函数***_mint***，该函数用来铸造代币。其有两个参数，第一个参数表示铸造代币的接收者地址，第二个参数表示要铸造代币的数额。

**Syntax**

function call

- 提示
    
    ```solidity
    _mint(msg.sender, 100);
    ```
    
