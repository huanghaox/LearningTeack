# Content/定义setPrice函数

刚刚提到我们还需要提供一个接口来改变这个***price***，这个函数相当于取代了价格预言机的功能，当然也简化了预测价格的难度，所以我们在这里定义一个***setPrice***函数来修改***price***。

因此我们需要一个`uint256`的参数来表示要修改的价格。

**Syntax**

function

- 提示
    
    ```solidity
    function setMoonShot(uint256 _price) public {}
    ```
    
