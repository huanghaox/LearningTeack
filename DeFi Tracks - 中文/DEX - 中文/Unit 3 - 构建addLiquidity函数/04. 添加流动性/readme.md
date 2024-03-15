# Content/添加流动性

在创建了if else分支后，我们先来处理if里的内容。

当储备量都为*0*时，我们会直接将指定数额的***_amountADesierd***和***_amountBDesierd***注入到流动性池中。

> 这个步骤一般是由开发者完成的，第一次注入的流动性将直接决定该交易对的交换价格。
> 

**注入流动性**的逻辑，我们将其抽象为了一个***_addLiquidity***函数，此函数会在下一节中讲到。

所以在这里我们只需要调用***_addLiquidity***函数并将要注入流动性池的两个代币的数量作为参数传入即可。

**Syntax Review**

function call

- 提示
    
    ```solidity
    add(amountA, amountB);
    ```
    
