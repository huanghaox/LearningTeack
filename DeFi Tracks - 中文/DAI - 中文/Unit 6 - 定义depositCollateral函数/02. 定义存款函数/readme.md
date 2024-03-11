# Content/定义存款函数

好了，我们已经定义好了变量和构造函数，接下来我们开始编写***depositCollateral***函数。

首先，我们要明白该函数的作用：用户通过该函数将指定数额的抵押物存进合约。

那么既然要指定数额，就一定需要一个参数来表示这个数额。在这里由于数额不可能是负数，我们选择使用`uint256`。

在函数可见性方面，因为这给函数是提供给用户调用的。所以我们选择`external`。

这个函数没有任何的返回值，因为他存入抵押物之后不需要接受任何的信息。

**Syntax**

function scope

- 提示
    
    ```solidity
    function deposit(uint256 amount) external {}
    ```
    
