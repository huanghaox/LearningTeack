# Content/引入ERC20和IERC20标准库

由于这是一个稳定币合约，而稳定币的实质其实也是一个遵循ERC20/IERC20标准的代币。

所以我们需要继承ERC20标准合约，这样，该合约就拥有了ERC20代币该有的所有功能。

要从现有库中使用ERC20和IERC20，我们需要完成三个步骤：

1. 导入ERC20和IERC20
2. 定义我们的合约以继承ERC20合约
3. 在构造函数中指定代币的名称和符号来初始化ERC20合约

目前，由Openzepplin开发的ERC20/IERC20合约是被业界广泛认可并使用的，它是声明代币的快速方式。

在这一节中，让我们先来引入Openzepplin的库吧~

**Syntax**

import

- 提示
    
    ```solidity
    import "@openzeppelin/contracts/...";
    ```
    
