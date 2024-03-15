# Content/添加流动性

让我们首先来编写 if 分支的内容。

如果 ***amountBOptimal*** 小于 ***_amountBDesired***，这意味着用户希望投入的金额中 A 代币的总价值小于 B 代币的总价值。在这种情况下，我们将会将 ***_amountADesired*** 和 ***amountBOptimal*** 作为流动性注入到流动性池中。

所以此时我们将***_amountADesierd***和***amountBOptimal***作为参数调用***_addLiquidity***函数即可。

***_addLiquidity***函数的作用就是实现流动性的添加以及Lp代币的生成，具体的逻辑我们会在后面进行讲解。

**Syntax**

function call

- 提示
    
    ```solidity
    add(amountA, amountB);
    ```
    
