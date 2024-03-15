# Content/定义calculateAmountB_swap函数

也许你应该已经明白了 ***calculateAmountB_swap*** 这个函数的作用，即计算给定数量的 A 代币可以交换成多少数量的 B 代币。

因此，我们需要一个参数来表示给定数量的 A 代币。对于可见性修饰符的选择，我们采用 public，因为该函数可以帮助所有人查询他们拥有的某个数量的 A 代币对应多少 B 代币。

由于这是一个查询函数，不会修改合约的属性，所以我们使用 `view` 关键字来声明。

最后，该函数应返回对应的 B 代币数量，因此我们需要一个 uint256 类型的返回值。

**Syntax**

function,scope

- 提示
    
    ```solidity
    function calculateAmountB(uint256 amount) public view returns (uint256) { }
    ```
    
