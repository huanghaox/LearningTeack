# Content/计算需要归还的抵押物数量

接下来我们就开始实现稳定币的偿还逻辑，首先我们需要计算出调用者准备归还的***stableCoinAmount***数量的稳定币对应多少抵押物余额。

这一步是通过**抵押率**来计算的。还记得我们在上一步从抵押物换取稳定币时也进行了一次换算吗，这里是相同的逻辑。我们需要将稳定币除以抵押物价格再乘上**抵押率**（***collateralRatio***除以*100*）的结果算出来并将其存储到一个局部变量中供后续逻辑中使用。

![未命名白板.jpg](./img/4-1.jpg)

**Syntax**

variable

- 提示
    
    ```solidity
    uint256 Collateral = amount * collateralRatio / 100 / price;
    ```
    
