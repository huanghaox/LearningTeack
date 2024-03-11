# Content/声明贷款金额

像上一章一样，我们在这里仍然建立一个映射用来记录用户贷款金额数量，依然是`address`到`uint256`，只不过这次我们不希望外人看见这个映射，因此可见性我们设置为`private`。

**Syntax**

mapping

- 提示
    
    ```solidity
    mapping(uint => address) private moonshot;
    ```