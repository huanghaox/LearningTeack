# Content/定义swapFromAToB函数

我们首先定义一个名为***swapFromAToB***的函数，其作用是将代币A交换为代币B。这个函数接受一个uint256类型的参数***amountA***，表示用户想要交换的代币A的数量。

在这个函数中，我们会执行代币交换的逻辑，将用户的代币A转换为对应的代币B。

为了使这个函数能够被其他合约或外部调用者使用，我们在可见性上选择了external。这意味着该函数可以从其他合约中调用，也可以从合约外部进行交互。

完成***swapFromAToB***函数后，我们还要按照相同的方式定义***swapFromBToA***函数，毕竟我们不能只把A换成B吧……

**Syntax**

function,scope

- 提示
    
    ```solidity
    function swapAToB(uint256 amountA) external { }
    ```
    
