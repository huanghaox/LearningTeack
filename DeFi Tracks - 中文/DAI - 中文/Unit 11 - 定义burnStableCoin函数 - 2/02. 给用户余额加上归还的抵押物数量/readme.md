# Content/给用户余额加上归还的抵押物数量

在计算完用户归还的这笔稳定币对应多少抵押物后，我们就可以进行后续的步骤了。

我们还需要将计算出的抵押物加在用户对应的抵押物余额映射***remainingCollateral***上，然后将这笔稳定币烧毁。

那么首先，我们先来给用户余额加上归还的抵押物。

**Syntax**

mapping

- 提示
    
    ```solidity
    remain[msg.sender] += returnedCollateral;
    ```
    
