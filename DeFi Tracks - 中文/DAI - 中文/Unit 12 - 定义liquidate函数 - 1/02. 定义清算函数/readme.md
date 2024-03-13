# Content/定义清算函数

让我们进入清算逻辑中，首先我们需要定义**清算**函数***liquidate***。

那么第一步你需要明白该函数的作用：根据指定的用户地址，判断该地址是否满足清算条件，如果满足清算，则执行清算逻辑。

所以我们需要一个`address`类型的入参来指定用户地址。

在函数可见性方面我们选择`external`，因为该函数需要提供给清算者，因为所有人都可以成为清算者。

**Syntax**

function scope

- 提示
    
    ```solidity
    function liquidate(address user) external { }
    ```
    
