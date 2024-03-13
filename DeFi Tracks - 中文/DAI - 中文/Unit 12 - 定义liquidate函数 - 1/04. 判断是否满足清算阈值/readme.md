# Content/判断是否满足清算阈值

在获取到抵押物的总价值后，我们就可以判断该地址是否满足清算阈值的要求了。

还记得清算阈值是怎么计算的吗？

抵押物总价值乘清算率如果大于当前贷款数额，则表明用户当前资金情况健康，不能被清算。反之，用户将被清算。

所以我们这里需要将抵押物总价值乘清算率的结果，与用户当前贷款的数额作比较。

![未命名白板.jpg](./img/4-1.jpg)

**Syntax**

require  mapping

- 提示
    
    ```solidity
    require(collateralValue * liquidationRatio / 100 < loanAmount[user], "error");
    ```
    
