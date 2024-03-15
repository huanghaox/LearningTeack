# Content/引入ERC20合约标准

由于我们正在构建一个自动化做市商模型，根据之前的讨论，提供流动性的用户将获得 LP 代币作为奖励。因此，我们需要定义一个 ERC20 代币，用于发放 LP 奖励。

目前，由Openzepplin开发的ERC20合约是被业界广泛认可并使用的。

让我们来引入Openzepplin的库吧~

**Syntax Review**

import

- 提示
    
    ```solidity
    import "@openzeppelin/contracts/...";
    ```
    
