# Content/定义_calculateAmountB_add函数

也许你应该已经明白了 ***_calculateAmountB*** 这个函数的作用，即计算给定数量的 A 代币可以应该相应地添加多少数量的 B 代币。

因此，我们需要一个参数来表示给定数量的 A 代币。对于可见性修饰符的选择，我们采用 internal ，因为我们希望这个函数只能是内部使用的。

由于这是一个查询函数，不会修改合约的属性，所以我们使用 `view` 关键字来声明。

最后，该函数应返回对应的 B 代币数量，因此我们需要一个 uint256 类型的返回值。

当然，知道了***_calculateAmountB_add***的定义，***_calculateAmountA_add***定义也就简简单单了！

**Syntax**

function,scope

- 提示
    
    ```solidity
    function set(uint256 amount) public view returns (uint256) { }
    ```
    
