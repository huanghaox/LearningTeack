# Content/定义烧毁稳定币函数

让我们直接进入***burnStableCoin***函数的定义吧，首先我们还是要明白该函数的作用。

该函数允许用户指定要归还的稳定币数量，函数内会将稳定币销毁，并将其转换为用户的抵押物余额。

所以我们需要一个`uint256`类型参数来表示用户想要归还的稳定币数量。

在可见性方面，和***mintStableCoin***对应，我们选择`external`。

**Syntax**

function scope

- 提示
    
    ```solidity
    function burn(uint256 amount) external { }
    ```
    
