# Content/定义取款函数

我们直接开始定义***withdrawCollateral***函数，在这里你首先要明白该函数的作用：用户归还稳定币之后调用该函数，可以将指定数量的抵押物从借贷合约中提取出来。

> 归还稳定币需要调用的函数会在后续章节中讲解。
> 

所以我们需要一个变量来表示取款的数额，同样，我们选择`uint256`。

在函数可见性方面，和***depositeCollateral***一样，这是一个提供给用户调用的函数，所以我们使用`external`。

***withdrawCollateral***函数和***depositeCollateral***一样没有返回值，因为我们不需要回复任何信息给用户。

**Syntax**

function scope

- 提示
    
    ```solidity
    function withdraw(uint256 _amount) external { }
    ```