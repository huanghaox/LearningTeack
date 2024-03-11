# Content/完善构造函数

完成所有的定义之后，我们现在开始实现具体的函数内容。

构造函数需要做两件事情

1. 初始化继承的ERC20合约
    
    我们在构造函数的头部已经完成了这一步。
    
2. 给状态变量赋值
    1. 将参数中`address`类型的***_collateralToken***通过IERC20初始化后赋值给IERC20类型的***collateralToken***。
    2. 将参数中`uint256`类型的***_collateralRatio***直接赋值给***collateralRatio***。
    3. 将参数中`uint256`类型的***_liquidationRatio***直接赋值给***liquidationRatio***。
    
    这样就完成了抵押物Token的赋值。
    

这样，构造函数的实现就完成了。

**Syntax**

variable

- 提示
    
    ```solidity
    constructor(address tokenAddress) {
        token = tokenAddress;
    }
    ```
    
