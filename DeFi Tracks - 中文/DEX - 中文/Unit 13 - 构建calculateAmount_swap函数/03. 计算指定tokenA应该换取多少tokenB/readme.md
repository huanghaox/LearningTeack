# Content/计算指定tokenA应该换取多少tokenB

定义完函数头后，让我们来完成函数体。

首先你必须理解自动化做市商模型AMM，这里我们模拟Uniswap的模型，也就是恒定乘积模型。

> 有关恒定乘积模型的更多概述请参阅DEX Concept
> 

恒定乘积模型中，代币的数量乘积 k 是永远保持不变的。因此，我们可以利用 k 除以 A 的储备量，再加上参与交换的代币 A 的数量，来计算交换后 B 代币的总数量。

【公式】

k = reverseA * reverseB

交换后B的总量 = k / (reverseA + amountA)

**Syntax**

variable

- 提示
    
    ```solidity
    uint256 totalAmount = k / (reverseA + amountA)
    ```
    
