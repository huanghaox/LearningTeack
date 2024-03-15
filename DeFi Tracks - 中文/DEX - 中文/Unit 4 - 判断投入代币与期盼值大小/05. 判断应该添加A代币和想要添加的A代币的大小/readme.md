# Content/判断应该添加A代币和想要添加的A代币的大小

接下来，我们来进入 else 分支。当进入该分支时，意味着用户希望投入流动性池的代币 A 的价值大于代币 B 的价值。

在这种情况下，我们不能直接将 ***_amountADesired*** 作为要投入流动性池的代币 A 的数量。相反，我们需要使用 ***_amountBDesired*** 来重新计算代币 A 应该投入的数量。

因此，我们需要将 ***_amountBDesired*** 作为参数调用 ***calculateAmountA*** 函数，以计算出与之等价的代币 A 的数量。

在所有这些计算中，我们始终保持一个核心原则：投入流动性池的两个代币的总价值必须相等。

> 因为我们不能破坏流动性池中两个代币的兑换比例。
> 

**Syntax**

function call

- 提示
    
    ```solidity
    calculate(amount);
    ```
    
