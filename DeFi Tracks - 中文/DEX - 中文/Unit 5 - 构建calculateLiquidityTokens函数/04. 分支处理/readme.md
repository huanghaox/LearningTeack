# Content/分支处理

在计算流动性代币的数量时，需要参考***reserveA***和***reserveB***的数量进行计算（相关内容在后续讲到）

因此，我们在这里需要分情况讨论

1. 在池尚未初始化时（***reserveA/B*** == 0）
2. 以及初始化（***reserveA/B*** ！= 0）

**Syntax**

variable

- 提示
    
    ```solidity
    uint moonshot = 520;
    ```
    
