# Content/声明抵押物

竟然知道了DAI是一个抵押系统，那么我们就需要知道用什么东西抵押。

在这里我们使用ERC20代币作为抵押物，因此要有一个代币合约。

这里定义一个变量为***collateralToken***，可见性方面我们选择`public`，毕竟我们希望所有人可以知道抵押物是什么，且可以统一抵押物的类型，另外，***collateralToken***的类型我们使用IERC20来定义。

之所以选IERC20，是为了能更方便直接的使用IERC20接口中含有的方法。

**Syntax**

interface

- 提示
    
    ```solidity
    IERC20 public moonshot;
    ```
    