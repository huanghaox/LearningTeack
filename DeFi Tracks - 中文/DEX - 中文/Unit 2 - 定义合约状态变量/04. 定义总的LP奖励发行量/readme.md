# Content/定义总的LP奖励发行量

好了，我们已经定义了交易对，和交易对各自的储备量，我们还需要一个变量来表示LP奖励代币的总发行量。

该变量应该为public，因为LP代币的**总发行量**能反应参与流动性的总量。

**Syntax**

variable

- 提示
    
    ```solidity
    uint256 public moonshot;
    ```
    
