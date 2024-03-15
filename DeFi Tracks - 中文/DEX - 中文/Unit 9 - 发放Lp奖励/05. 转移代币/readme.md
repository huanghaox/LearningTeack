# Content/转移代币

好的，到目前为止，我们已经完成了添加流动性的逻辑处理。

然而，在最后，我们不要忘记将用户添加的流动性代币转移到流动性池中（这是关键！）。

由于我们已经定义了流动性代币对的地址，我们可以直接使用 ***IERC20*** 接口来进行操作。通过调用 ***transferFrom*** 函数，我们可以将代币从流动性提供者转移至流动性池中

**Syntax**

function call,interface

- 提示
    
    ```solidity
    IERC20(token).transferFrom(from, to, amount);
    ```
    
