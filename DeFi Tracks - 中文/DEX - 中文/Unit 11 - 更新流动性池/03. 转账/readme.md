# Content/转账

刚刚我们分别计算出了用户应该提取的代币对数量***amountA***和***amountB***。

现在我们可以将这笔资金转给用户，我们需要使用IERC20接口以调用***tokenA***和***tokenB***的***transfer***函数，并将***amountA***和***amountB***作为参数传入。

在前面我们已经使用require对条件进行了限制，在这里，我们再、仍然可以用*require*对上面转账进行一下限制！

它的作用是：要求转账必须成功才能继续之后的步骤！

**Syntax**

function call , interface

- 提示
    
    ```solidity
    IERC20(token).transfer(msg.sender, amount);
    ```
    
