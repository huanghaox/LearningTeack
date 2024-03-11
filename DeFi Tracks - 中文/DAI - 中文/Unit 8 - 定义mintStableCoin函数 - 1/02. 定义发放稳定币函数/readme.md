# Content/定义发放稳定币函数

让我们就可以开始定义***mintStableCoin***函数吧，首先我们还是要先理解这个函数要做什么。

该函数的目的是通过抵押物换取稳定币，所以我们需要一个`uint256`类型的变量来指定要将多少**抵押物**置换为**稳定币**。

函数可见性方面，我们依然选择使用`external`，因为该函数是提供给用户调用的。

**Syntax**

function

- 提示
    
    ```solidity
    function mintCoin(uint256 amount) external {}
    ```
    
