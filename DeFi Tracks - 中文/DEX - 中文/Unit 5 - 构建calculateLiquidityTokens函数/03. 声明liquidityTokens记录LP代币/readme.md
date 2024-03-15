# Content/声明liquidityTokens记录LP代币

关于返回值，由于该函数需要计算用户应该获得的 LP 奖励，因此我们需要定义一个返回值来表示它。在本节中，我们将使用已命名的返回值方式，在返回值中定义一个 uint256 类型的变量 ***liquidityTokens***。这样，在函数体内，我们只需要给 ***liquidityTokens*** 赋值即可，而无需使用 return 语句。

**Syntax**

variable

- 提示
    
    ```solidity
    uint moonshot = 520;
    ```
    
