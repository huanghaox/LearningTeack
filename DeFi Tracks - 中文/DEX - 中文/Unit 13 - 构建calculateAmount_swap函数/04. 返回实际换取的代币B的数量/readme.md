# Content/返回实际换取的代币B的数量

一旦我们获取到交易后的 B 代币总数，计算本次交换所获得的 B 代币数量就变得轻而易举。

由于我们正在交换出 B 代币，所以我们可以通过将 B 的储备量减去交易后的 B 代币总数来获得交换到的 B 代币数量。

最后，使用 return 语句将这个值作为函数的返回值即可。

另外，竟然已经知道了如何把A换成B，那我们仿照***calculateAmountB_swap***的完成方式来定义***calculateAmountA_swap***函数吧！

**Syntax**

return

- 提示
    
    ```solidity
    return reserve - total;
    ```
    
