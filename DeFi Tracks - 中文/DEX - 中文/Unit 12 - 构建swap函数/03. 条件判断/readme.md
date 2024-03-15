# Content/条件判断

刚刚我们定义出了***swapFromAToB***函数，那么首先我们还是需要进行一个条件控制。

在***swapAToB***中，需要将***amount***数量的A转移给合约并换取B。因此我们首先需要判断用户代币A的余额大于***amount***。 

在这里我们使用require语句，并通过IERC20的***balanceOf***函数获取用户代币A的余额。

**Syntax**

require

- 提示
    
    ```solidity
    require(IERC20(a).balanceOf(account) >= amount);
    ```
    
