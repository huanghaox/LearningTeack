# Content/定义储备量

在定义完***tokenA***和***tokenB***两个表示代币的变量后，还记得我们提到过的储备量这个概念吧。

储备量是指当前代币在流动性池中存放的总量。

我们需要分别定义***tokenA***的储备量和***tokenB***的储备量。

可见性的选择上我们使用public，因为储备量作为直接反应系统“健康状态”的指标，需要公开透明。

**Syntax Review**

variable

- 提示
    
    ```solidity
    uint256 public moonshot;
    ```
    
